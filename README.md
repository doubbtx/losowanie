# Losowanie prezentów

Strona do świątecznego losowania (Kamil, Mateusz, Paweł, Sabina, Asia, Julia, Adrian) i głosowania na budżet prezentu.
Działa na GitHub Pages, a dane trzyma w darmowej bazie Firebase (Firestore).

## Podłączenie (ok. 10 minut)

### 1. Firebase
1. Wejdź na https://console.firebase.google.com i kliknij **Utwórz projekt** (np. `losowanie-prezentow`). Google Analytics możesz wyłączyć.
2. **Build → Authentication → Get started → Sign-in method → Anonymous → Enable → Save.**
3. **Build → Firestore Database → Create database**, wybierz lokalizację `europe-central2 (Warsaw)` i **Start in production mode**.
4. W Firestore przejdź do zakładki **Rules**, usuń wszystko, wklej zawartość pliku `firestore.rules` i kliknij **Publish**.
5. **Ustawienia projektu (zębatka) → General → Your apps →** ikona `</>` (Web). Podaj dowolną nazwę i NIE zaznaczaj Hostingu. Skopiuj obiekt `firebaseConfig`.
6. Otwórz `index.html`, znajdź blok `WKLEJ TUTAJ SWOJĄ KONFIGURACJĘ FIREBASE` i podmień wartości `"WKLEJ"` na swoje.
   Te klucze nie są tajne, mogą być publicznie w repozytorium. Bazę chronią reguły z kroku 4.

### 2. GitHub Pages
1. Na https://github.com/new utwórz **publiczne** repozytorium, np. `losowanie`.
2. **Add file → Upload files**, przeciągnij `index.html` (już z twoją konfiguracją), `firestore.rules` i `README.md`, potem **Commit changes**.
3. **Settings → Pages → Source: Deploy from a branch → Branch: `main`, folder `/ (root)` → Save.**
4. Po 1–2 minutach strona będzie pod adresem `https://TWOJ-LOGIN.github.io/losowanie/`.

### 3. Dopuszczenie domeny w Firebase
**Authentication → Settings → Authorized domains → Add domain** i wpisz `TWOJ-LOGIN.github.io`.
Bez tego logowanie anonimowe nie zadziała.

Gotowe. Wyślij link znajomym.

## Ważne
- Każdego rozpoznajemy po przeglądarce. Kto otworzy stronę w innej przeglądarce, na innym telefonie albo w trybie incognito, może wylosować drugi raz. Niech każdy losuje tylko raz, na jednym urządzeniu.
- Kto wyczyści dane przeglądarki, straci podgląd swojego wyniku, a imię zostaje zajęte. Warto zrobić zrzut ekranu po zatwierdzeniu.
- **Reset / test:** w Firebase w **Firestore → Data** usuń kolekcje `taken` i `draws` (losowanie) oraz `votes` (głosy).
- Jeśli ostatniej osobie zostanie w puli tylko jej własne imię, trzeba zresetować losowanie.
