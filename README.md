# Analiză State-of-the-Art: Unelte de Asigurare a Calității pentru Java

## 1. Introducere

Lucrarea de față se bazează pe articolul _"A Comprehensive Study on Quality Assurance Tools for Java"_ (ISSTA 2023), care oferă o analiză detaliată asupra a șase unelte de Quality Assurance (QA) utilizate frecvent în proiecte Java: **SonarQube**, **SpotBugs**, **Error Prone**, **Infer**, **PMD** și **Semgrep**. Scopul principal este **determinarea celui mai eficient tool QA** pentru uzul studenților la facultate, pe baza unor criterii de ușurință în utilizare, performanță, acuratețe a avertismentelor și integrabilitate în workflow-ul de dezvoltare.

## 2. Obiective

- Rularea și configurarea celor șase unelte QA pe aplicația de E-ticketing, folosind **IntelliJ IDEA Community Edition** ca mediu de dezvoltare. 
- Colectarea și compararea numărului de avertismente și a ratei de „true positives” pentru fiecare tool.  
- Măsurarea timpilor de execuție și evaluarea complexității setup-ului.  
- Analiza calitativă și cantitativă a rezultatelor pentru a desemna **cel mai potrivit tool** pentru proiecte studențești.

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

## 6. Articole științifice similare

Pe lângă studiul principal de la ISSTA 2023, am consultat și alte lucrări relevante:

- Studiul realizat de **Lenarduzzi et al.** oferă o comparație detaliată între șase unelte ASAT. Autorii notează că SonarQube detectează cea mai mare parte dintre problemele comune, dar între unelte există puțină suprapunere:

  > "SonarQube is the one able to detect most of the quality issues that can be detected by the other ASATs. However, [...] there is little to no agreement among the tools, indicating that different tools are able to identify different forms of quality problems."  

- În analiza efectuată de **Yeboah & Popoola**, accentul este pus pe precizia detecției. Rezultatele arată că SonarQube are cea mai mare precizie dintre toate uneltele testate:

  > "SonarQube had the highest precision of 0.79 followed by Checkstyle with a precision of 0.60, while FindBugs had the lowest precision of 0.33."  

- Conform cercetării lui **Khatami & Zaidman**, gradul de maturitate al proiectelor open-source influențează aplicarea tehnicilor de asigurare a calității:

  > "More mature projects are more intense in their application of the quality assurance practices, with more focus on their ASAT usage, and code reviewing, but no strong change in their CI usage."  

## 7. Descărcare și Utilizare a Uneltelor QA

În această secțiune descriem pașii de instalare și rulare pentru fiecare tool. La finalul fiecărei explicații se află capturi de ecran reprezentative.

<details>
<summary>SonarQube</summary>
<br>
  Versiune: 10.22.0.81244
  
  **Instalare în IntelliJ IDEA (Community/Ultimate):**  
1. Mergi la **File → Settings → Plugins** (sau `Ctrl+Alt+S`).  
2. Deschide tab-ul **Marketplace**, caută **“SonarQube for IDE”** (de la SonarSource) și apasă **Install**.  
3. Repornește IDE.

**Configurare conexiune la server SonarQube:**  
1. În **File → Settings → Tools → SonarQube** → **Connections**, click pe **+** și adaugă:  
   - **Name:** `LocalSonar`  
   - **Server URL:** `http://localhost:9000`  
   - **Token:** `<token-ul tău>`  
2. În **Project Settings** apasă **Bind** și selectează proiectul tău din server.

**Utilizare:**  
1. În **Project View**, dă click-dreapta pe rădăcina proiectului → **SonarQube → Analyze Project**.  
2. Așteaptă finalizarea analizei; vei vedea problemele listate în panoul **SonarQube**.  
3. Pentru export:
   - Click pe iconița de **Export** (în colțul dreapta-sus al panoului SonarQube).  
   - Alege **Export as HTML** sau **Export as XML** și salvează în `docs/screenshots/sonarqube-report.html` (sau `.xml`).

**Imagini**

  ![image](https://github.com/user-attachments/assets/4e7f7b13-db44-4368-b673-97f87d0597aa)
  Figura 1 - eroarea detectata de tool-ul SonarQube intr-un proiect Java
  
</details>


<details>
<summary>SpotBugs</summary>
<br>
Versiune: 1.2.8

**Instalare în IntelliJ IDEA (Community/Ultimate):**
1. Mergi la **File → Settings → Plugins** (sau `Ctrl+Alt+S`).
2. Click pe **Marketplace**, caută **“SpotBugs”** (plugin-ul “spotbugs-idea”) și apasă **Install**.
3. Repornește IDE.

**Utilizare:**  
1. În **Project View**, dă click-dreapta pe rădăcina proiectului → **SpotBugs → Analyze with SpotBugs**.  
2. După finalizarea analizei, fereastra de rezultate va arăta lista de bug-patterns găsite.  
3. Poți exporta raportul astfel:
   - Click pe iconița de **Export** (în colțul dreapta-sus al ferestrei SpotBugs Results).
   - Alege **Export as HTML** sau **Export as XML** și salvează.

**Imagini**

![SpotBugs2](https://github.com/user-attachments/assets/9516657e-afc3-4a14-90b2-2fab2a860626)
Figura 2 - erorile detectate de tool-ul SpotBugs

</details>


<details>
<summary>ErrorProne</summary>
<br>
  Versiune: 243.21565.129
  
  **Instalare în IntelliJ IDEA (Community/Ultimate):**  
1. Mergi la **File → Settings → Plugins** (sau `Ctrl+Alt+S`).  
2. Deschide tab-ul **Marketplace**, caută **“Error Prone Compiler”** și apasă **Install**.  
3. După instalare, mergi la **File → Settings → Build, Execution, Deployment → Compiler → Java Compiler** și selectează la **Use compiler** opțiunea **`Javac with error-prone`**.  
4. Repornește IDE.

**Utilizare:**  
1. Orice compilare (Build → Build Project) va fi interceptată de Error Prone.  
2. Erorile şi warning-urile vor apărea în panoul **Problems** și marcate direct în editor.

**Imagini**

  ![image](https://github.com/user-attachments/assets/4f63b67c-68e2-419c-b49a-823d1478a3d8)
  Figura 3 – eroarea detectata de tool-ul Error Prone intr-un proiect Java
  
</details>


<details>
<summary>PMD</summary>
<br>
  Versiune: 2.0.6

  **Instalare în IntelliJ IDEA (Community/Ultimate):**
  1. Mergi la **File → Settings → Plugins** (sau `Ctrl+Alt+S`).
  2. Click pe **Marketplace**, caută **“PMD”** și apasă **Install**.
  3. Repornește IDE.

**Utilizare:**  
1. În **Project View**, dă click-dreapta pe rădăcina proiectului → **Run PMD → Check code with PMD**.  
2. Așteaptă până PMD scanează întregul cod; rezultatele apar într-un panou **PMD**.  
3. Pentru export:
   - Click pe iconița de **Export** (în colțul stanga-jos al ferestrei PMD Results).  
   - Alege **Export as HTML** sau **Export as XML** și salvează.
  
**Imagini**
![PMD2](https://github.com/user-attachments/assets/a6ed4859-6c20-4b20-873f-e479ad2c1669)
Figura 4 - eroarea detectata de tool-ul PMD intr-un proiect Java

</details>


<details>
<summary>Semgrep</summary>
<br>
  Versiune: 1.122.0
  
  Semgrep nu există ca plugin direct în IntelliJ, așa că vom rula analiza local folosind CLI:

  1. **Urmează ghidul oficial CLI**  
      https://theinfosecguy.medium.com/how-to-install-semgrep-a-comprehensive-guide-for-developers-4531b8eb3754

  2. **Exemplu de rulare cu Docker**  
     ```bash
     # Descarcă imaginea oficială
     docker pull semgrep/semgrep

     # Scanează tot proiectul
     docker run --rm \
       -v "$(pwd)":/src \
       semgrep/semgrep \
       semgrep --config auto /src
     ```

**Imagini**

![image](https://github.com/user-attachments/assets/c6ce89dc-ae23-4a84-be3b-1026938dc866)
Figura 5 - eroarea detectata de tool-ul Semgrep

</details>


<details>
<summary>Postman</summary>
<br>
  Versiune: ?
  TO-DO
  
  **Imagini**
  
  ![image](https://github.com/user-attachments/assets/73c02548-e1ae-448d-a9b6-ec9a9b3dad89)
  Figura 6 - rezultatul obtinut in urma cererii in Postman
</details>


## 8. Concluzii asupra uneltelor QA testate

După rularea și compararea a șase unelte de asigurare a calității pe proiectul E-ticketing, tragem următoarele concluzii:

- **SonarQube**  
  - **Puncte tari:** acoperire largă a regulilor CWE, dashboard web intuitiv, integrare CI/CD.  
  - **Puncte slabe:** necesită setare inițială (server/Docker), execuție mai lentă pe proiecte mari.  
  - **Recomandare:** ideal pentru proiecte de echipă și pipeline-uri de laborator.

- **SpotBugs**  
  - **Puncte tari:** detecție precisă de bug-patterns (null-pointer, concurență), integrare Maven/IDE facilă.  
  - **Puncte slabe:** acoperire mai redusă față de SonarQube, necesita configurare a rule-set-ului.  
  - **Recomandare:** excelent ca prim tool pentru studenți, datorită simplității și preciziei.

- **Error Prone**  
  - **Puncte tari:** interceptare la compilare, feedback imediat în editor, zero‐config.  
  - **Puncte slabe:** acoperire CWE limitată, depinde de API-ul Java compiler.  
  - **Recomandare:** folosit împreună cu SpotBugs pentru validări compile-time rapide.

- **PMD**  
  - **Puncte tari:** rulare foarte rapidă, multitudine de reguli, suport Maven/CLI.  
  - **Puncte slabe:** multe false positives (cod style și documentație), necesită filtrare.  
  - **Recomandare:** util pentru verificări rapide de stil și practici, în combinație cu alte tool-uri.

- **Postman**  
  - **Puncte tari:** interfață intuitivă și testare rapidă API.
  - **Puncte slabe:** dependență de configurații complexe de mediu.
  - **Recomandare:** ideal pentru testare rapidă a API-urilor.
 
- **Semgrep**  
  - **Puncte tari:** reguli customizabile, focus pe securitate și pattern-matching.  
  - **Puncte slabe:** cea mai lentă execuție, configurare YAML obligatorie.  
  - **Recomandare:** pentru laboratoare avansate de securitate și reguli proprii.

---

**Sinteză recomandări pentru studenți:**  
- **Prim tool:** SpotBugs – instalare și rulare simple, alertă de calitate precisă.  
- **Completare compile-time:** Error Prone – feedback imediat la cod.  
- **Verificări stil & practici:** PMD – rapid, multe reguli.  
- **Audit avansat & securitate:** SonarQube & Semgrep – pentru proiecte mari și reguli custom.  
- **Audit memorie/concurență:** Infer – pentru case study punctuale.  ??


## 9. Raport despre folosirea unui tool de AI

**Avantaje**

* Feedback rapid: am trimis o parte dintr-un cod Java, iar ChatGPT mi-a identificat instant eroarea de tip NullPointerException din metoda de calcul și mi-a explicat cauza.
* Explicații clare: pe lângă diagnostic, am primit pași concreți de reparare (verificarea obiectelor înainte de folosire și adăugarea de Optional).
* Generare automată de teste: ChatGPT mi-a sugerat un set de cazuri JUnit pentru a acoperi și scenarii de eroare.

**Dezavantaje**

* Context limitat: modelul nu a știut despre setup-ul complet al proiectului meu Maven și a sugerat o configurație generică de dependințe.
* Risc de informații inexacte: uneori recomandă API-uri care nu există în versiunea curentă a bibliotecilor pe care le folosesc.
* Necesită verificare umană: soluțiile propuse trebuie testate și adaptate manual înainte de integrare în CI.

**Recomandări**

* Sa se verifice informatiile furnizate acolo unde se poate, mai ales in zona de securitate cibernetica.
* Sa se foloseasca doar pentru prototiparea rapidă a testelor, apoi sa se refactorizeze manual.


## 10. Diagrame
TO-DO

## 11. Video
TO-DO

## 12. Referinţe

1. Valentina, Lenarduzzi, _A Critical Comparison on Six Static Analysis Tools: Detection, Agreement, and Precision_, arXiv, [online], [url](https://arxiv.org/pdf/2101.08832), accesat la 9 aprilie 2025.  
2. Jones, Yeboah, _Efficacy of static analysis tools for software defect detection on open-source projects_, arXiv, [online], [url](https://arxiv.org/pdf/2405.12333), accesat la 9 aprilie 2025.  
3. Ali, Khatami, _State-Of-The-Practice in Quality Assurance in Java-Based Open Source Software Development_, arXiv, [online], [url](https://arxiv.org/pdf/2306.09665), accesat la 9 aprilie 2025.  
4. OpenAI, ChatGPT, [https://chatgpt.com/](https://chatgpt.com/), generare conținut: 9 aprilie 2025.
