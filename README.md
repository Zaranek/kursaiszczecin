# 🎨 Moje portfolio AI 2.0

Gotowy szablon cyfrowego portfolio dla uczniów. **Bez instalacji pakietów, bez Reacta, bez bazy danych.** Strona wykrywa nowe prace automatycznie po każdej publikacji GitHub Pages z użyciem GitHub Actions.

## Start — najpierw nauczyciel

1. Utwórz **nowe publiczne repozytorium** na GitHubie, np. `portfolio-ai-template`.
2. Prześlij **zawartość tego folderu** (nie sam plik ZIP). Koniecznie razem z ukrytym folderem `.github/workflows/` oraz folderami `skrypty`, `generator` i `materialy`.
   - **Uwaga**: przy zwykłym przesyłaniu plików przez witrynę GitHub mogą wystąpić trudności z ukrytym folderem `.github`. Najpewniejszy sposób: pobierz ZIP, rozpakuj i prześlij przy użyciu aplikacji GitHub Desktop / `git`, albo stwórz plik `.github/workflows/pages.yml` przez interfejs GitHub. W repozytorium musi pozostać zachowana ta sama struktura.
3. Wybierz **Settings → Pages → Build and deployment → Source → GitHub Actions** (to bardzo ważne: **nie** `Deploy from a branch`).
4. W zakładce **Actions** uruchom `Opublikuj portfolio AI → Run workflow`, albo dokonaj zmiany i zatwierdź commit. Jeśli zobaczysz przycisk włączenia workflows, włącz je.
5. Kiedy proces skończy się zielonym symbolem, otwórz `Settings → Pages → Visit site`.
6. W **Settings → General** zaznacz **Template repository**, by uczniowie mogli użyć `Use this template`.

> **Jeżeli masz już repozytorium z poprzednią stroną**, przed migracją zachowaj jego kopię. Wgrywając nową wersję, trzeba podmienić `index.html` i dodać pozostałe pliki. Zmień też źródło publikacji w Pages na **GitHub Actions**.

## Start — uczeń

1. Otwórz repozytorium-szablon nauczyciela i wybierz **Use this template → Create a new repository**.
2. Wybierz **Public**, nadaj nazwę (np. `moje-portfolio-ai`) i utwórz repozytorium.
3. Otwórz **Settings → Pages → Source → GitHub Actions**.
4. Otwórz zakładkę **Actions**; w razie potrzeby wybierz **Enable workflows**. Uruchom workflow `Opublikuj portfolio AI` ręcznie poprzez **Run workflow** albo zapisz dowolną zmianę w `main`.
5. Po zakończeniu publikacji otwórz adres `https://TWOJ-LOGIN.github.io/moje-portfolio-ai/`.
6. Usuń przykładowe prace, kiedy dodasz własne.

**Uwaga:** po zmianie `main` i katalogów prace publikowane są przez własny workflow. Publikacja zwykle trwa chwilę; sprawdź jej stan w Actions. Nie przesyłaj poufnych danych ani prywatnych zdjęć innych osób.

## Zasada folderów — 2 przypadki

### A) Jeden plik luzem = jeden projekt

Prześlij np. plik `pies.png` do katalogu `materialy/grafiki/`:

```text
materialy/
  grafiki/
    pies.png         ← 1 projekt na stronie, automatycznie!
    kot.png          ← 2 projekt na stronie, automatycznie!
```

Na stronie zobaczysz karty „Pies” oraz „Kot”. Możesz przeglądać i pobierać ich zawartość. **Nie edytuj HTML ani app.js.**

Opcjonalnie generator tworzy opis `pies.png.json`, który umieszczasz **obok zdjęcia**:

```text
materialy/grafiki/
  pies.png
  pies.png.json      ← tytuł, opis, narzędzia, prompt...
```

### B) Jeden podfolder = jeden projekt z wieloma plikami

```text
materialy/
  komiksy/
    moja-historia/           ← jeden projekt
      okladka.png
      plansza-01.png
      plansza-02.png
      narracja.mp3
      projekt.json           ← opcjonalny opis całego folderu
```

Program odnajdzie pliki wewnątrz folderu i pokaże je w jednej karcie. Nawet bez `projekt.json` projekt będzie działał. **Podfolder projektu musi leżeć bezpośrednio w katalogu kategorii.**

## Dostępne kategorie

| Folder GitHub | Nazwa na stronie |
|---|---|
| `materialy/grafiki/` | Grafiki |
| `materialy/teksty/` | Teksty |
| `materialy/dzwiek/` | Dźwięk i muzyka |
| `materialy/filmy/` | Filmy i animacje |
| `materialy/komiksy/` | Komiksy |
| `materialy/strony-www/` | Strony i aplikacje WWW |
| `materialy/gry/` | Gry |
| `materialy/techniczne-3d/` | Projekty techniczne i 3D |
| `materialy/analizy-prezentacje/` | Analizy i prezentacje |

## Generator opisów — bez pisania JSON

Otwórz na swojej stronie adres `.../generator/`, następnie:

- **Opis pojedynczego pliku** — podaj jego ścieżkę, np. `materialy/grafiki/pies.png`. Formularz pobierze `pies.png.json`. Wgraj go do `materialy/grafiki/`.
- **Opis całego folderu** — podaj `materialy/komiksy/moja-historia`. Formularz pobierze `projekt.json`. Wgraj do `materialy/komiksy/moja-historia/`.
- **Edytuj profil** — zmień imię, zdjęcie, zainteresowania, umiejętności. Formularz pobierze `profil.json`. Wgraj go do **głównego katalogu** repozytorium i zastąp stary.

Generator pozwala również wczytać już utworzony opis JSON i go zmienić. **Generator sam niczego nie wysyła na GitHub.** Wszystkie modyfikacje plików zatwierdzasz przez GitHub.

Przykład `projekt.json`:

```json
{
  "tytul": "Moja bajka",
  "opis": "Krótka historia z ilustracjami i narracją.",
  "narzedzia": ["ChatGPT", "Canva"],
  "miniatura": "okladka.png",
  "prompt": "Napisz bajkę dla młodszych uczniów...",
  "refleksja": "Nauczyłem się tworzyć spójnych bohaterów."
}
```

Jeśli chcesz tylko wyświetlić nowy plik, **wcale nie potrzebujesz generatora**. Samo wrzucenie pliku do folderu kategorii wystarczy.

## Formaty i pobieranie

- Obrazy: `.png .jpg .jpeg .svg .gif .webp .avif`
- Audio: `.mp3 .wav .ogg .m4a`
- Wideo: `.mp4 .webm`
- Dokumenty: `.pdf .txt .md .docx .pptx .xlsx .csv .odt .odp .ods`
- Kod i materiały techniczne: `.html .css .js .py .ino .stl .step .stp .dxf .glb .gltf .obj .zip` (i kilka pokrewnych).
- Duży film, gra lub prezentacja online: opcjonalny `link` HTTPS w `projekt.json` (także folder zawierający sam opis i link może być projektem).

Odwiedzający może pobierać publiczne pliki bez logowania. W zależności od rodzaju pliku i przeglądarki może nastąpić jego otwarcie zamiast pobrania — wówczas można użyć menu pobierania przeglądarki.

**Zalecenie na kurs:** grafiki do ok. 5 MB, dokumenty/audio do ok. 20 MB, duże filmy zamieszczaj jako linki. Przeglądarkowy upload GitHub ma własne limity; duże binaria nie nadają się do przechowywania w historii Git.

## Testowanie lokalne (dla nauczyciela)

Otwórz terminal w katalogu repozytorium i wykonaj:

```bash
python skrypty/buduj.py
cd _site
python -m http.server 8000
```

Otwórz `http://localhost:8000`. Bez `http.server` niektóre przeglądarki blokują wczytywanie JSON z dysku (`file://`).

## Szybka diagnoza błędów

- **Błąd wczytywania katalogu?** GitHub Pages musi być ustawione na **GitHub Actions**, a workflow musi skończyć się poprawnie.
- **Nie widać nowego pliku?** Sprawdź, czy `Commit changes` został zatwierdzony, czy plik jest w `main` oraz we właściwym katalogu `materialy/kategoria/`.
- **Wszystkie pliki jednego folderu są jednym projektem?** Tak, to zamierzone.
- **Osobna strona gry nie działa?** Najlepiej opublikować grę jako samodzielne GitHub Pages lub umieścić cały projekt w folderze wraz z `index.html` i wszystkimi wymaganymi zasobami (odnośniki względne!).
- **Opisy nie działają?** Dla pojedynczego pliku opis musi się nazywać dokładnie `nazwa.ext.json`; dla folderu `projekt.json`.
- **Zdjęcie profilowe nie działa?** Wgraj je na GitHub i podaj w profilu poprawną ścieżkę, np. `assets/ja.jpg`.
- **Puste foldery zniknęły?** GitHub nie przechowuje pustych folderów; pliki `.gitkeep` utrzymują ich obecność.

## Bezpieczeństwo

Repozytorium oraz publikowana strona są **publiczne**. Nie przechowuj haseł, kluczy API ani prywatnych danych. Generator opisów nie ma dostępu do konta GitHub i nie wysyła plików. GitHub Actions wykonuje skrypt Pythona **podczas publikacji**, nie na komputerze ucznia ani podczas przeglądania strony.

Zgodność z licencjami materiałów i zgodami na publikację wizerunku pozostaje odpowiedzialnością autora portfolio.
