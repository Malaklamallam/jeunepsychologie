``` mermaid
%% Diagramme de classes – Accès aux soins psychologiques pour les jeunes (93)
classDiagram

class Youth {
  UUID id
  String firstName
  String lastName
  Int age
  String city
  String schoolStatus
  Bool gdprConsent
  +requestHelp(channel String)
  +chooseStructure(structureId UUID)
  +evaluateSatisfaction(score Int)
}

class SchoolInstitution {
  UUID id
  String name
  String typeInstitution
  String city
  String schoolPsychologistContact
  +detectYouth(y Youth) Bool
  +refer(y Youth, s MedicoSocialStructure)
  +informFamily(y Youth)
}

class HealthProfessional {
  UUID id
  String fullName
  String specialty
  String workMode
  String rpps
  String availability
  +evaluate(y Youth)
  +consult(y Youth, date Date) Consultation
  +writeReport(c Consultation, text String)
}

class Psychologist
class Psychiatrist
Psychologist --|> HealthProfessional
Psychiatrist --|> HealthProfessional

class MedicoSocialStructure {
  UUID id
  String name
  String structureType
  String address
  String phone
  String area
  Int capacity
  +welcome(y Youth)
  +openFile(y Youth) FollowUpFile
  +coordinateCare(y Youth)
  +referToHospital(y Youth, h Hospital)
}

class CMP
class MDA
CMP --|> MedicoSocialStructure
MDA --|> MedicoSocialStructure

class Hospital {
  UUID id
  String name
  String department
  String address
  Int capacity
  +admit(y Youth)
  +hospitalize(y Youth, days Int)
  +ensureFollowUp(y Youth)
}

class PsychologicalProgram {
  UUID id
  String name
  String targetPopulation
  Int maxSessions
  +checkEligibility(y Youth) Bool
  +generateReferral(y Youth) Referral
  +fundConsultation(c Consultation) Bool
}

class ARS_IDF {
  UUID id
  String name
  String region
  Float mentalHealthBudget
  +fund(s MedicoSocialStructure, amount Float)
  +planHealthcareOffer(area String)
  +authorizeOpening(s MedicoSocialStructure) Bool
}

class LocalAuthority {
  UUID id
  String name
  String authorityType
  Float preventionBudget
  +subsidize(a LocalAssociation, amount Float)
  +launchPreventionCampaign(school SchoolInstitution)
}

class LocalAssociation {
  UUID id
  String name
  String domain
  String city
  +raiseAwareness(y Youth)
  +support(y Youth)
  +refer(y Youth, s MedicoSocialStructure) Referral
}

class FollowUpFile {
  UUID id
  Date openingDate
  String status
  List~String~ goals
  +addGoal(text String)
  +close()
  +shareWith(actor String)
}

class Consultation {
  UUID id
  Date date
  String type
  String location
  Int durationMinutes
  String report
  +addReportText(text String)
  +assignYouth(y Youth)
  +assignProfessional(p HealthProfessional)
}

class Referral {
  UUID id
  Date date
  String origin
  String destination
  String status
  +validate()
  +trackStatus() String
}

%% Relations principales
Youth ..> Consultation
HealthProfessional ..> Consultation
Youth ..> FollowUpFile
MedicoSocialStructure ..> FollowUpFile
SchoolInstitution ..> MedicoSocialStructure
LocalAssociation ..> MedicoSocialStructure
MedicoSocialStructure ..> Hospital
PsychologicalProgram ..> HealthProfessional
ARS_IDF ..> MedicoSocialStructure
LocalAuthority ..> LocalAssociation
Youth ..> PsychologicalProgram
```
