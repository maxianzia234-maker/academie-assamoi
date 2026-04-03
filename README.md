https://github.com/maxianzia234-maker/academie-assamoi.git
Academie Assamoi
export function FormationsPage({ inscrireCours }) {
  const cours = [
    "Pharmacie 101",
    "Biologie Avancée",
    "Mathématiques pour Pharma",
  ];

  return (
    <div className="grid md:grid-cols-3 gap-6">
      {cours.map((c, i) => (
        <div key={i} className="border p-6 rounded-lg shadow hover:shadow-lg">
          <h4 className="font-bold text-xl mb-2">{c}</h4>
          <button
            onClick={() => inscrireCours(c)}
            className="mt-4 px-4 py-2 bg-slate-900 text-white rounded-2xl"
          >
            S'inscrire
          </button>
        </div>
      ))}
    </div>
  );
}
export function PaiementInscriptionPage() {
  return (
    <div className="border p-6 rounded-lg shadow max-w-md mx-auto text-center">
      <h3 className="text-2xl font-bold mb-4">Paiement et inscription</h3>
      <p className="mb-6">Pour accéder au cours, effectuez le paiement sécurisé.</p>
      <button className="px-6 py-3 bg-green-600 text-white rounded-2xl shadow hover:bg-green-700">
        Payer maintenant
      </button>
    </div>
  );
}
export function EspaceEtudiantDashboard() {
  const cours = ["Pharmacie 101", "Biologie Avancée", "Mathématiques pour Pharma"];
  return (
    <div>
      <h3 className="text-3xl font-bold mb-6 text-center">Mon Espace Étudiant</h3>
      <ul className="space-y-4">
        {cours.map((c, i) => (
          <li key={i} className="border p-4 rounded-lg shadow hover:shadow-lg flex justify-between items-center">
            <span>{c}</span>
            <button className="px-3 py-1 bg-blue-600 text-white rounded-2xl">Accéder au cours</button>
          </li>
        ))}
      </ul>
    </div>
  );
}
export function LecteurCoursVideo() {
  const chapitres = [
    "Introduction",
    "Chapitre 1 - Concepts de base",
    "Chapitre 2 - Applications pratiques",
  ];

  return (
    <div className="max-w-3xl mx-auto">
      <h3 className="text-3xl font-bold mb-6 text-center">Lecteur vidéo</h3>
      <video className="w-full rounded-lg mb-6" controls>
        <source src="/videos/exemple.mp4" type="video/mp4" />
        Votre navigateur ne supporte pas la lecture vidéo.
      </video>
      <div className="space-y-2">
        {chapitres.map((chap, i) => (
          <div key={i} className="flex justify-between items-center border p-2 rounded hover:bg-slate-100">
            <span>{chap}</span>
            <a href={`/pdf/${chap}.pdf`} download className="text-blue-600 hover:underline">
              Télécharger PDF
            </a>
          </div>
        ))}
      </div>
    </div>
  );
}
import { useState } from "react";

export function QuizInteractif({ terminerQuiz }) {
  const questions = [
    { q: "Quelle est la formule chimique de l'eau ?", options: ["H2O", "CO2", "O2"], answer: "H2O" },
    { q: "Combien de chromosomes humains ?", options: ["46", "23", "44"], answer: "46" },
  ];

  const [score, setScore] = useState(0);
  const [current, setCurrent] = useState(0);

  const handleAnswer = (option) => {
    if (option === questions[current].answer) setScore(score + 1);
    if (current + 1 < questions.length) setCurrent(current + 1);
    else terminerQuiz();
  };

  return (
    <div className="max-w-xl mx-auto border p-6 rounded-lg shadow text-center">
      {current < questions.length ? (
        <>
          <h4 className="text-xl font-bold mb-4">{questions[current].q}</h4>
          <div className="space-y-2">
            {questions[current].options.map((opt, i) => (
              <button
                key={i}
                onClick={() => handleAnswer(opt)}
                className="block w-full px-4 py-2 bg-slate-900 text-white rounded-2xl hover:bg-slate-700"
              >
                {opt}
              </button>
            ))}
          </div>
        </>
      ) : (
        <h4 className="text-2xl font-bold">Quiz terminé ! Votre score: {score}/{questions.length}</h4>
      )}
    </div>
  );
}
