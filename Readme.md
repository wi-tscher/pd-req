# Kraven för utveckling av PocketDemocracy

Detta GitHub repository (sv. förvar, förkortat repo), är ett versioneringssystem
för kraven av pocketdemocracy. Det är också ett kollaborativ plattform för fil 
editering (tyvärr bara textfiler). Det är möjligt att editera filerna också i
webb-vyn (vid <https://github.com/[denna_repo]>).

Kraven i HTML form kan hittas [här](/artifacts/html/RequirementsDoc.html).

## Projekthantering

GitHub stöder också så kallade Issues, med vilka man kan hantera ett projekt;
ifall ett problem (eng. issue) uppstår lagar man en Issue i GitHub, och
relevant personal blir anmälda om problemet. I Issue-vyn kan man också föra
diskussioner i diskussionskädjor, och man kan länka mella olika diskussioner,
enligt behov.

# Valet av verktyg

RMTOO är ett Kommando-tolk-program (CLI tool, Command Line Interface tool). Den
tar in filer, och matar ut filer. En typ av filer den matar ut är En PDF fil,
eller en HTML-fil med alla kraven (requirement) strukturerade under ämnen
(topic). För tillfället är det ändast witscher@abo.fi som kan processera
in-filerna med hjälp av ```rmtoo``` (setup av programmet är inte trivialt).

## Mappstruktur

Ett rmtoo projekt (alla projekt i princip) har krav (requirements, sparas i
filer med filändelsen '.req'), ämnen (topics, sparas i filer med filändelsen
'.tic') och begränsningar (constraints, sparas i filer med filändelsen '.ctr').
Varje filkategori sparas i sin egna mapp med motsvarande namn.

# Filformat

Krav-, ämnes- och bergränsnings-filerna har ett mycket simpelt filformat.
Formatet uppstår av mycket simpla nyckel-värde-par (key-value pair).

## Hur man fyller i REQ-filer (Requirement, krav)

Från RMTOO manualen (```man rmtoo-req-format```):

### KEY 'Priority'
    
    Each requirement must have a priority.  The effective priority is computed by the currently given priority multiplied by a normalized maximum priority of all parents.
    
    The format is 'stakeholder:num'. 'num' must be a number between and including 0 and 10.  It is possible to specify more than one stakeholders separating them with a space.

### KEY 'Effort estimation'
    The effort estimation is done with the help of an abstract measurement so called 'effort points'. These effort points are used in agile processes (especially SCRUM) to get a prediction about the burn-down speed and the expected finished date.

    0 - no effort
    1 - tiny effort
    2 - very small effort (two times a tiny effort)
    3 - small effort (same as a tiny and a very small effort)
    5 - medium effort (same as a very small and a small effort)
    8 - big effort (same as a small and a medium effort)
    13 - very big effort (same as big effort and a medium effort)
    21 - huge effort (same as very big effort and big effort)

### KEY 'Rationale'
    This is optional. This gives a hint and some more details about the requirement. Typically some background information is given here.

### KEY 'Note'
    The note is an additional comment for the requirement.

### KEY 'Solved by'
    Each requirement which is 'solved' by other requirements must have one or more children. The 'Solved by' tag contains a list of these children.

### KEY 'Status'
    The status can be one of 'not done' or 'finished'.

### KEY 'Topic'
    This is the topic this requirement belongs to.

### KEY 'Class'
    This gives the class of the requirement. Currently two values are possible 'detailable', 'implementable' or 'selected':

    'detailable' means that the requirement must be elaborated before they can be implemented.

    'implementable' means that the requirement is detailed enough to start with implementation.

    'selected' means  that  the requirement is selected for the next sprint. Based on this selection the sprint burndown and the selected table is printed.

## Hur man fyller i TIC-filer (Topic, ämne)

### KEY 'Name'
    The value is the name of the topic.  This is used as a chapter headline in the output document.

### KEY 'Text'
    The text value will be copied into the output document.

### KEY 'IncludeRequirements'
    This  is the position where all the requirements are inserted in the output document.  The value must be the string 'full'.

### KEY 'SubTopic'
    The value of the subtopic must be the id of another topic.  This topic is inserted at  the  point  of  occurance.

## CTR-filer (Constraints, begräsningar)

rmtoo tillåter testning av krav (dvs. inte testning av kod men av rmtoo-krav).
För tillfället finns det inga funktionerande tester för krav i constraints.
Detta är också mindre viktigt i detta skedet, åtminstone jämfört med att
formulera klara krav.