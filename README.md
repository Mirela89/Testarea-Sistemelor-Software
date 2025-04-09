# Analiză State-of-the-Art: Unelte de Asigurare a Calității pentru Java

## 1. Introducere

Lucrarea de față se bazează pe articolul _"A Comprehensive Study on Quality Assurance Tools for Java"_ (ISSTA 2023), care oferă o analiză detaliată asupra a șase unelte de Quality Assurance (QA) utilizate frecvent în proiecte Java: **SonarQube**, **SpotBugs**, **Error Prone**, **Infer**, **PMD** și **Semgrep**. Scopul acestei faze este realizarea unei versiuni incipiente (alpha-alpha) a proiectului, prin colectarea resurselor, analiza aplicațiilor existente și pregătirea mediului de lucru.

## 2. Definiții esențiale

- **Quality Assurance Tools**: unelte software folosite pentru detectarea automată a bug-urilor, defectelor sau a practicilor de programare necorespunzătoare.
- **Scanning Rules**: reguli utilizate de aceste unelte pentru a analiza codul sursă.
- **CWE (Common Weakness Enumeration)**: standard internațional pentru clasificarea slăbiciunilor software.
- **Granularitate a regulilor**: nivelul de detaliere cu care o unealtă de QA își definește regulile de scanare, determinând capacitatea acesteia de a detecta nu doar probleme generale, ci și defecte specifice.

## 3. Articol științific utilizat

- **Titlu**: _A Comprehensive Study on Quality Assurance Tools for Java_
- **Conferință**: ISSTA 2023
- **Autori**: Han Liu et al.
- **Link**: [https://doi.org/10.1145/3597926.3598056](https://doi.org/10.1145/3597926.3598056)
- **Unelte analizate**: SonarQube, SpotBugs, Error Prone, Infer, PMD, Semgrep

## 4. Analiza aplicațiilor existente

| Tool       | Scop                       | Avantaje                                   | Dezavantaje                            |
|------------|----------------------------|--------------------------------------------|----------------------------------------|
| SonarQube  | Analiză calitate cod       | Acoperire CWE mare, interfață web          | Timp de execuție ridicat pe proiecte mari |
| SpotBugs   | Detectare bug-uri Java     | Granularitate bună                          | Nu acoperă toate domeniile             |
| Error Prone| Detectare greșeli la compilare | Rulat la compilare, rapid               | Acoperire parțială CWE                 |
| Infer      | Detectare pointeri/memorie | Detectează bug-uri punctuale               | Timp de execuție ridicat               |
| PMD        | Detectare defecte simple    | Rapid, multe reguli                         | Avertismente adesea irelevante         |
| Semgrep    | Detectare generică + securitate | Reguli extensibile, personalizabile     | Cel mai lent, acoperire redusă         |

## 5. Întrebări de cercetare abordate

- **RQ1: Acoperirea și granularitatea regulilor**
  - SonarQube și Error Prone acoperă mai multe categorii CWE.
  - Infer, SpotBugs și Semgrep oferă o granularitate mai detaliată.

- **RQ2: Detectarea bug-urilor**
  - Testarea pe 1.425 de bug-uri arată o medie de doar 10% rată de detectare pentru cele mai bune unelte (PMD, SonarQube).

- **RQ3: Eficiența avertismentelor**
  - Majoritatea avertismentelor nu indică bug-uri reale, dar pot semnala riscuri utile (ex: dereferențiere nulă).

- **RQ4: Performanța**
  - PMD este cel mai rapid.
  - Semgrep are timp mare de execuție, dar e scalabil datorită procesării paralele.

## 6. Resurse și servicii identificate

- Toate uneltele sunt open-source.
- Fiecare are documentație oficială.
- Suportă integrarea în CI/CD: GitHub Actions, Jenkins, GitLab CI etc.

## 7. Articole științifice similare

Pe lângă studiul principal de la ISSTA 2023, am consultat și alte lucrări relevante:

- Studiul realizat de **Lenarduzzi et al.** oferă o comparație detaliată între șase unelte ASAT. Autorii notează că SonarQube detectează cea mai mare parte dintre problemele comune, dar între unelte există puțină suprapunere:

  > "SonarQube is the one able to detect most of the quality issues that can be detected by the other ASATs. However, [...] there is little to no agreement among the tools, indicating that different tools are able to identify different forms of quality problems."  

- În analiza efectuată de **Yeboah & Popoola**, accentul este pus pe precizia detecției. Rezultatele arată că SonarQube are cea mai mare precizie dintre toate uneltele testate:

  > "SonarQube had the highest precision of 0.79 followed by Checkstyle with a precision of 0.60, while FindBugs had the lowest precision of 0.33."  

- Conform cercetării lui **Khatami & Zaidman**, gradul de maturitate al proiectelor open-source influențează aplicarea tehnicilor de asigurare a calității:

  > "More mature projects are more intense in their application of the quality assurance practices, with more focus on their ASAT usage, and code reviewing, but no strong change in their CI usage."  

## 8. Concluzii parțiale

Această etapă inițială a oferit o înțelegere clară a uneltelor QA pentru Java. S-au identificat diferențe importante în ceea ce privește acoperirea, granularitatea regulilor și performanța în timp. Aceste informații vor ghida implementarea și testarea ulterioară a sistemului.

## 9. Referinţe

1. Valentina, Lenarduzzi, _A Critical Comparison on Six Static Analysis Tools: Detection, Agreement, and Precision_, arXiv, [online], [url](https://arxiv.org/pdf/2101.08832), accesat la 9 aprilie 2025.  
2. Jones, Yeboah, _Efficacy of static analysis tools for software defect detection on open-source projects_, arXiv, [online], [url](https://arxiv.org/pdf/2405.12333), accesat la 9 aprilie 2025.  
3. Ali, Khatami, _State-Of-The-Practice in Quality Assurance in Java-Based Open Source Software Development_, arXiv, [online], [url](https://arxiv.org/pdf/2306.09665), accesat la 9 aprilie 2025.  
4. OpenAI, ChatGPT, [https://chatgpt.com/](https://chatgpt.com/), generare conținut: 9 aprilie 2025.
