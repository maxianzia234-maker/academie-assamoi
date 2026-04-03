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
