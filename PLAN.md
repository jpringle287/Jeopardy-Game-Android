Week 1 — UI Shell (UI First)

Goal: Static screens + navigation with placeholders. No real data.

Tasks (Issues)
	•	#1 Create HomeActivity with “Play” button.
	•	#2 Create BoardFragment with 5×5 grid (categories/values).
	•	#3 Create QuestionFragment with question, answer input/buttons, timer placeholder.
	•	#4 Set up Navigation Component, safe args, and base theme.
	•	#5 Add placeholder resources (colors, typography, icons).

Branches & Commits
	•	feat/ui-home:
	•	feat(ui): add HomeActivity with play CTA
	•	feat/ui-board:
	•	feat(ui): add BoardFragment with 5x5 grid and stub cells
	•	feat/ui-question:
	•	feat(ui): add QuestionFragment layout with prompt and timer placeholder
	•	chore/nav:
	•	chore(nav): configure nav graph and safe args
	•	chore/theme:
	•	chore(ui): base theme, typography, and color resources

Test Steps (on device/emulator)
	1.	Launch app → verify Home screen loads.
	2.	Tap Play → navigates to Board.
	3.	Tap any placeholder cell → navigates to Question screen.
	4.	Back navigation returns to Board, then Home.
	5.	Rotate device → screens keep layout (no crashes).

⸻

Week 2 — Stubs: Data Models & Repositories

Goal: Create data contracts and stub repositories; show mock data on UI.

Tasks (Issues)
	•	#6 Define models: Category, Clue, RoundState, ScoreState.
	•	#7 Create Repository interface (GameRepository) with functions:
	•	getCategories(), getClues(categoryId), getClue(categoryId, value).
	•	#8 Implement MockRepository with hardcoded JSON or in-memory lists.
	•	#9 Wire BoardFragment to render mock categories and values.
	•	#10 Wire QuestionFragment to consume mock clue for selected cell.

Branches & Commits
	•	feat/stub-models:
	•	feat(model): add Category, Clue, RoundState, ScoreState
	•	feat/stub-repo:
	•	feat(data): add GameRepository contract and MockRepository
	•	feat/ui-binding:
	•	feat(ui): bind BoardFragment to mock categories
	•	feat(ui): load mock clue on QuestionFragment

Test Steps
	1.	Board shows 5 categories × 5 values from mock repo.
	2.	Tapping a cell displays a real mock question text.
	3.	“Back” returns to the same board state (even if not persisted yet).
	4.	No crashes across rotations.

⸻

Week 3 — Glue: ViewModels, State, and Basic Scoring

Goal: Add ViewModels to coordinate UI with repository; implement basic score updates and one-round flow.

Tasks (Issues)
	•	#11 Add BoardViewModel and QuestionViewModel (LiveData/StateFlow).
	•	#12 Introduce ScoreManager (in domain/ or util/).
	•	#13 Mark clue as “used” after it’s opened; disable it on the board.
	•	#14 Add simple answer flow (show “Reveal” → mark correct/incorrect).
	•	#15 Show temporary toast/snackbar for scoring feedback.

Branches & Commits
	•	feat/vm-board:
	•	feat(vm): add BoardViewModel with category and clue state
	•	feat/vm-question:
	•	feat(vm): add QuestionViewModel with current clue and answer check
	•	feat/scoring:
	•	feat(domain): add ScoreManager and basic scoring updates
	•	refactor/ui-bindings:
	•	refactor(ui): disable used cells and update board state

Test Steps
	1.	Pick a clue → question screen appears.
	2.	Tap Correct → score increases by clue value; Incorrect → decreases.
	3.	Return to board → that clue is disabled/marked “used.”
	4.	Finish several clues → score accumulates correctly.

⸻

Week 4 — Engine: Timer, Persistence, Round Summary

Goal: Add timer (engine behavior), persist board/score locally, and show a Round Summary.

Tasks (Issues)
	•	#16 Implement TimerEngine (countdown with pause/resume).
	•	#17 Add local persistence (SharedPreferences or Room/SQLite for state).
	•	#18 Create RoundSummaryFragment with final score and stats.
	•	#19 “New Game” resets state cleanly.

Branches & Commits
	•	feat/engine-timer:
	•	feat(engine): add countdown timer with lifecycle-safe callbacks
	•	feat/persistence:
	•	feat(data): persist score and used clues (SharedPreferences/Room)
	•	feat/summary:
	•	feat(ui): add RoundSummaryFragment and new game flow

Test Steps
	1.	Timer starts on question display; when it ends, auto-mark incorrect (or lock answering).
	2.	Kill app → relaunch → board and score restore.
	3.	After N clues (or “End Round”), summary screen shows correct/incorrect counts and final score.
	4.	“New Game” clears state and returns to a fresh board.

⸻

Week 5 — Polish: Animations, Sounds, Accessibility

Goal: UX polish + basic accessibility.

Tasks (Issues)
	•	#20 Add simple cell reveal animation and button press feedback.
	•	#21 Integrate sound effects (correct/incorrect, timer).
	•	#22 Add content descriptions, larger tap targets, and color contrast updates.
	•	#23 Improve empty/error states for data loading.

Branches & Commits
	•	feat/ux-animations:
	•	feat(ui): add animations for clue reveal and board transitions
	•	feat/ux-sound:
	•	feat(ui): integrate AudioManager sounds
	•	chore/a11y:
	•	chore(a11y): add contentDescription and touch target sizing

Test Steps
	1.	Verify animations don’t block interaction; app remains responsive.
	2.	Sounds play appropriately and are muted by Android’s silent mode.
	3.	Use TalkBack to ensure elements announce properly.
	4.	No regressions from Week 1–4.

⸻

Week 6 — README, Screenshots, and MVP Tag

Goal: Make the repo recruiter-ready.

Tasks (Issues)
	•	#24 Add screenshots (/screenshots/) and update README.
	•	#25 Write “What I learned” + “Future Work” sections.
	•	#26 Tag MVP release v0.1.0 and attach APK (optional).

Branches & Commits
	•	docs/readme:
	•	docs: update README with screenshots and setup
	•	chore/release:
	•	chore(release): tag v0.1.0 and attach debug apk

Test Steps
	1.	README has clear Overview → Features → Setup → Screenshots.
	2.	APK (optional) installs and runs on emulator or Android device.
	3.	All core MVP flows function without crashes.
