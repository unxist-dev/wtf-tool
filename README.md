# wtf — *what the fuck: jestem w tym repo?*

```
	       ▄█                  ▄█
███   ███ █▀▀███▀▀█   ▄█▀▀███
▓▓▓   ▓▓▓    █▓▓  ▀ ▄▓▓   ▀▀▀
▒▒▒ ▄ ▒▒▒    ▒▒▒    ▒▒▒▀▀    
░░░ █ ░░░    ░░░    ░░░      
 ▀▀▀▀▀▀▀     ▀▀▀    ▀▀▀

````


Wracasz do projektu po tygodniu, urlopie albo skakaniu między repozytoriami. Otwierasz terminal, robisz `cd` i nie pamiętasz, na czym stanęła robota.

`wtf` odpowiada na to pytanie jednym poleceniem. Bez konfiguracji, daemonów, `npx`, `docker pull` czy wstępnego setupu.

## Co pokazuje

1. **Repo** — aktualny branch, ostatni commit oraz status ahead/behind względem upstreamu.
2. **Working tree** — stan plików (untracked / modified / staged) skrócony do zwięzłego `--shortstat`.
3. **Ostatnie commity** — 10 ostatnich wpisów z krótkim hashem i względnym czasem ("X days ago").
4. **Aktywne pliki (7 dni)** — lista plików najczęściej modyfikowanych w ostatnim tygodniu.
5. **Roadmapa / notatki** — wyciąga pliki `.md`/`.txt` z roota i katalogu `docs/`. Pliki typu `ROADMAP`, `TODO`, `NOTATKI` czy `PLAN` wyświetla bezpośrednio w terminalu (do 22 linii), pozostałe tylko listuje.
6. **TODO / FIXME w kodzie** — szybki `grep` po popularnych rozszerzeniach (top 15 wyników w formacie `plik:linia`).

Kolejność informacji jest celowa: od kontekstu "gdzie jestem", przez stan zmian, po historię i zaległe zadania.

## Instalacja

Wymaga Ruby 2.7+ (używa `Enumerable#tally`) oraz `git` w `PATH`. Zero zewnętrznych gemów.

```fish
mkdir -p ~/bin
# Zapisz skrypt jako ~/bin/wtf
chmod +x ~/bin/wtf

```

Dla **fish** (`~/.config/fish/config.fish`):

```fish
fish_add_path $HOME/bin

```

Dla **bash / zsh** (`~/.bashrc` lub `~/.zshrc`):

```bash
export PATH="$HOME/bin:$PATH"

```

## Użycie

```bash
wtf          # Przegląd aktualnego repozytorium
wtf ~/code/foo # Przegląd innego repozytorium (bez przechodzenia do niego)

```

Skrypt nie ma flag, subkomend ani `--help`. Jeśli zapomnisz, jak działa: `head -20 ~/bin/wtf`.

## Czym NIE jest ten tool

* **Nie jest dashboardem** — brak TUI, braki kolorowych tabel, brak odświeżania co sekundę. Jeden strzał, jeden ekran tekstu i powrót do sh.
* **Nie integruje się z GitHubem/Jirą** — nie strzela do API po PR-y, issue czy stan CI. Działa w 100% lokalnie i offline.
* **Nie zgaduje typu projektu** — nie analizuje `package.json` ani `Cargo.toml`. Wymaga jedynie zainstalowanego Gita.
* **Nie modyfikuje repozytorium** — działa wyłącznie w trybie odczytu (read-only).

## Filozofia

Jeden plik. Zero zależności. Zero konfiguracji. Ma działać od razu po dodaniu do `PATH` i nadaniu praw do wykonywania.

## Licencja

MIT / Do whatever you want. Jeśli coś nie działa — kod jest krótki, napraw go pod swoje potrzeby.
