<img width="2842" height="3362" alt="mermaid" src="https://github.com/user-attachments/assets/551ea684-8c89-4bb9-a1e1-4f3b4c88a769" />


classDiagram
%% --- Acteurs principaux ---
class ARS_IDF {
  +String nom = "Agence Régionale de Santé Île-de-France"
  +coordonnerPolitiqueSante()
  +financerStructures()
}

class Departement93 {
  +String nom = "Département de la Seine-Saint-Denis"
  +soutenirDispositifsLocaux()
  +coordonnerActeurs()
}

class CMP {
  +String nom
  +String localisation
  +int nb_psychologues
  +suiviPsychologique(Jeune)
  +orientation(Jeune)
}

class PJSM {
  +String nom = "Plateforme Jeunesse Santé Mentale"
  +accompagnement(Jeune)
  +orientation(Famille)
}

class Association {
  +String nom
  +String domaine
  +prevention(Jeune)
  +soutien(Famille)
}

class EducationNationale {
  +String nom = "Éducation nationale"
  +signalement(Jeune)
  +preventionEcoles()
}

class Jeune {
  +String nom
  +int age
  +String situation
  +demandeAide()
  +participerSuivi()
}

class Famille {
  +String nom
  +String lienJeune
  +demandeInformation()
  +soutenirJeune()
}

class ODDS93 {
  +String nom = "Observatoire Départemental des Données Sociales"
  +collecterDonnees()
  +analyserDonnees()
}

class PTSM93 {
  +String nom = "Projet Territorial de Santé Mentale 93"
  +partagerDonnees()
  +evaluerStructures()
}

class CapitalisationSante {
  +String nom = "Capitalisation Santé"
  +diffuserPratiquesInnovantes()
}

%% --- Relations ---
ARS_IDF --> Departement93 : planifie et finance
Departement93 --> CMP : coordonne
Departement93 --> PJSM : soutient
CMP --> Jeune : assure le suivi psychologique
PJSM --> Jeune : oriente et accompagne
Association --> Jeune : propose écoute et prévention
Association --> Famille : offre soutien
EducationNationale --> PJSM : collabore pour la prévention
EducationNationale --> CMP : signale jeunes en difficulté
ODDS93 --> PTSM93 : transmet données
PTSM93 --> CapitalisationSante : partage résultats
CapitalisationSante --> ARS_IDF : diffuse retours d’expérience
Famille --> PJSM : demande accompagnement
Jeune --> CMP : sollicite un suivi

