# MatchStats – Aplikacja do organizacji meczów piłkarskich i prowadzenia statystyk

MatchStats to aplikacja mobilna wspomagająca organizację nieprofesjonalnych meczów piłkarskich. Jej celem jest połączenie w jednym narzędziu funkcji organizacji spotkań, komunikacji oraz prowadzenia szczegółowych statystyk zawodników i drużyn. Aplikacja została opracowana w technologii Flutter z wykorzystaniem backendu Firebase (Authentication, Cloud Firestore, Storage), dzięki czemu działa szybko, jest skalowalna i umożliwia aktualizację danych w czasie rzeczywistym.

## MatchStats ma na celu:
- ułatwić organizację amatorskich meczów,
- dać graczom możliwość prowadzenia własnych statystyk,
- wspierać rozwój zawodników poprzez historię postępów,
- ułatwić komunikację między uczestnikami meczu,
- dostarczyć emocji i profesjonalizmu nawet w grach rekreacyjnych.

# Funkcje aplikacji
## Utworzenie konta w aplikacji
- Konta użytkowników
	- Tworzenie profilu zawodnika (imię, nazwisko, kontakt, avatar).
	- Rejestracja przez formularz lub konto Google.
	- Logowanie przez e-mail lub Google Authentication.
	- Edycja profilu (czy udostępniać media społecznościowe w celu kontaktu, zdjęcie, status dostępności, czy chętny do gry).

## Organizacja spotkań
- Tworzenie meczu:
  - Podanie daty, godziny (z kalendarza) i miejsca (tekstowo).
  - Ustawienie maksymalnej liczby zawodników w składzie.
  - Wybór drużyn – ręcznie lub poprzez losowanie.
  - Opcja „Dołącz do meczu” – otwarte spotkania dla innych zawodników.

- Zarządzanie meczem:
  - Edycja składu, daty i miejsca.
  - Dodawanie, usuwanie zawodników, statystyków i widzów.
  - Ustawianie statusów dostępności zawodników.
  - Możliwość dodania meczu do Google Kalendarza.

## Statystyki zawodników i drużyn
- Statystyki indywidualne:
  - Gole
  - Asysty
  - Strzały celne i niecelne
  - Strzały w słupek/poprzeczkę
  - Faule
  - Dryblingi
  - Dośrodkowania
  - Żółte i czerwone kartki
  - Liczba meczów

- Statystyki drużynowe:
  - Automatycznie wyliczane na podstawie statystyk indywidualnych.
  - Porównanie drużyn w ramach jednego meczu.

## Relacja na żywo i statystycy
- Rola statystyka:
	- Statystyk wprowadzający dane podczas meczu:
		- aktualizuje wynik,
		- rejestruje wydarzenia meczowe w czasie rzeczywistym.
	- Rozpoczęcie meczu uruchamia w bazie czasomierz meczu.
	- Zakończenie meczu blokuje możliwość edycji.

- Weryfikacja danych:
	- Po meczu kapitanowie obu drużyn potwierdzają statystyki.
	- Możliwość oceny pracy statystyka.

## Widzowie i relacja meczu
- Podgląd wyniku i statystyk na żywo.
- Lista zawodników i skład drużyn.
- Podgląd czasu trwania meczu.
- Dostęp do historii spotkań.

## Multimedia i interakcje po meczu
- Dodawanie zdjęć do galerii meczu.
- Komentarze uczestników.
- Ocena zawodników w trzech kategoriach:
	- umiejętności,
	- fair play,
	- konfliktowość.

## Wyszukiwanie i historia
- Wyszukiwanie meczu po:
	- ID spotkania,
	- nazwie drużyny.
- Historia wszystkich meczów użytkownika (w tym filtrowanie spotkań na podstawie daty oraz roli).
- Dostęp do statystyk ogólnych i indywidualnych.

## System
Zapewnia wysoki stopień walidacji danych, takich jak:
- Sprawdzanie adresu email podczas rejestracji, w celu uniknięcia kont o takich samych adresach
- Podczas tworzenia spotkania:
  - jeden zawodnik przypisany do jednej drużyny
  - jeden kapitan w drużynie
  - uzupełnienie wszystkich informacji na temat spotkania
- Historia spotkań:
  - wyświetlanie tylko tych meczów w których uczestniczył użytkownik oraz ewenutalna filtracja
- Wprowadzanie statystyk:
  - brak możliwość edycji po zakończeniu spotkania (jedyny wyjątek kapitanowie obu zespołów w celu weryfikacji statystyk)
  - statystyki drużynowe są automatycznie aktualizowane przez zmiany statystyk indywidualnych, co zwiększa dokładność danych oraz uniemożliwa "oszukanie" wyniku
  - sprawdzenie, czy wprowadzone statystyki oraz wynik zostały odczytane oraz potwierdzone przez kapitanów obu zespołów (konieczność zapozniania się kapitana z ewentualnymi zmianami umożliwia akcpetację)
##
 
## Architektura systemu
- Warstwa kliencka (Flutter)
	- logika UI/UX,
	- komunikacja z Firebase,
	- prezentacja i aktualizacja danych.

- Backend (Firebase)
	- Authentication – logowanie e-mail/Google,
	- Firestore – przechowywanie danych:
		- użytkownicy,
		- mecze,
		- statystyki,
		- komentarze,
		- role,

- Storage – zdjęcia profilowe, multimedia meczowe.

- Baza danych (Firestore NoSQL)
- Główne kolekcje:
	- users – dane zawodników i statystyki,
	matches – struktura meczów i danych meczowych.

- Model uwzględnia:
	- statystyki graczy,
	- kompletny opis meczu,
	- uczestników,
	- dostępność,
	- zdjęcia,
	- komentarze,
	- role użytkowników.

## Przykładowy przebieg meczu w aplikacji
- Użytkownik tworzy spotkanie oraz skład drużyn.
- Zawodnicy przekazują swoją dostępność w danym spotkaniu kapitanowi.
- Wybór składu przez kapitanów.
- Statystyk rozpoczyna spotkanie.
- W trakcie gry na bieżąco dodaje zdarzenia meczowe.
- Widzowie śledzą wynik i statystyki na żywo.
- Zakończenie spotkania przez statystyka.
- Uczestnicy dodają zdjęcia, komentarze, oceny.
- Kapitanowie potwierdzają wprowadzone dane po zakończeniu meczu.
- Statystyki zapisują się w historii zawodników i drużyn.

## Możliwości Rozwoju
- Dodanie czatu
- Wybór miejsca spotkanie na podstawie map np. GoogleMaps
