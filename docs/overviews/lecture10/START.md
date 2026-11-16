# Run this lesson

This folder contains the source PDF, authored lesson, portable HTML, local KaTeX, and a local AI service. Keep the folder together.

## Read and edit

Use Hide to collapse the left contents panel. A fixed Contents tab remains on the left edge; click it or Show contents in the header to reopen it. Alt+T also toggles it while reading. Explicitly reopened contents stay visible beside the note editor and library.

- Open index.html for reading, demos, notes, and mindmaps without a model service.
- Edit lesson.html for course content, lesson.json for metadata and mindmap guides, and lesson.js / lesson.css for subject-specific demos.
- Run python3 build.py after editing. A changed content revision creates a separate browser record. Export notes before replacing a revision; keep its original page with the backup.

## Pi tutor

Install pi separately if it is not available. In a terminal, run pi, configure /login and /model using your provider, and exit. From this lesson folder:

~~~sh
python3 serve.py --backend pi
~~~

Open http://127.0.0.1:8789/. Reading works immediately; the first question starts one real pi RPC process. Pi keeps its tools, installed extensions, skills, and saved conversation. The bridge appends a lesson tutor prompt and sends the course reference filename, current question, and only new or changed discussion entries.

Options:

~~~sh
python3 serve.py --backend pi --port 8790 --pi-cwd /path/to/lesson
~~~

- LESSON_PI_EXECUTABLE: pi executable or full path.
- LESSON_PI_MODEL: optional provider/model override; otherwise use pi's configured model.
- LESSON_PI_EXTENSIONS: optional JSON array of additional extension paths, only if not already discovered by pi.
- --pi-state-dir: override the private session directory.

The default working directory is this lesson folder. The default state directory is .lesson-pi/<document-id>/<revision>/. Different lessons and revisions therefore use different sessions. One session belongs to one browser notebook. Use the same browser address, or import its backup into an empty notebook to preserve its identity. Another learner needs a separate state directory.

If pi reports duplicate tools, inspect its extension/package configuration and keep one implementation of each tool. This template does not impose the original author's package filters or provider.

## Compatible API

~~~sh
export LESSON_LLM_BASE_URL='https://your-provider.example/v1'
export LESSON_LLM_MODEL='your-model-id'
export LESSON_LLM_API_KEY='your-key'
python3 serve.py --backend api
~~~

The key stays in the service environment. This route uses Chat Completions with the lesson and complete earlier browser discussion. It has no pi tools and no automatic fallback from pi.

## Context and backups

Questions and notes open in a right sidebar, so the lesson stays readable. Send saves a question and requests its answer immediately; Save note keeps a note without requesting an answer. Drafts save automatically and survive closing the editor, selecting another passage, and reloading. Ctrl/Command+Enter performs the primary action; Escape closes the editor. More → Send later saves a question for later, with Send now on its record. When the LLM is unconfigured, the local service is offline, or pi/model requests fail, questions stay pending in the waiting queue with their original context. Queue → View waiting questions opens the list; Retry sends one question and Queue → Send waiting questions sends the list. Queue contents survive reload and JSON backup/import. Connecting or reloading does not send questions automatically. Sending a new question does not send deferred questions. More → Send waiting questions explicitly sends the waiting list; Alt+Enter also sends that list while reading.

The browser saves notes, questions, answers, attempts, themes, panel layout, and mindmaps in localStorage, isolated by document ID, revision, and origin. Export notes downloads JSON; Import merges the same lesson revision. Changing ports or browsers creates another record.

A question can include selected prose, original TeX, nearby context, chapter and nested section, exercise/solution/attempt, the current demo snapshot, and earlier discussion. Rectangle capture reads underlying HTML rather than screenshot pixels. Figure alternative text is available to the tutor; pixels are not automatically interpreted.

The pi state directory saves the full agent session, discussion backup, and completed-answer receipts. Completed question retries reuse the saved answer; interrupted tool work may need inspection before retrying. Exported browser JSON does not include pi tool logs or files created by tools.

Check connection verifies local service configuration and lesson revision, without making a model request. It does not establish provider authentication. The service listens on 127.0.0.1 and does not serve hidden paths. Restart the service after rebuilding.

The backend uses Python 3.10+ and its standard library on macOS/Linux. Pi uses its own provider and login; a local bridge does not imply local model inference.

## Find and manage saved records

Open Notes & questions from the top bar or Contents, or choose Notes in the bottom toolbar. The library opens all blocks by default; search text, quoted passages, answers, or a record number, then filter by block or type. Chapter previews show recent records with direct Edit note and Delete controls.

Edit note updates the saved wording while keeping its original passage and record number. Delete moves the whole record, including its follow-ups, to Trash. Use Undo delete or choose Trash and Restore; deletions and recovery survive reload. Trash records are included in exports for recovery, and importing an older backup does not undo newer edits or deletions.

Deleted records are removed from reading highlights and the pending queue, and are omitted from the discussion sent with new questions. Pi receives note changes, deletions, and restorations on the next question. Previously sent turns remain in its saved session transcript.

## Mindmap controls

- Use − / + to zoom, click the percentage to return to 100%, or choose Fit map to show the complete graph. Ctrl/Command + wheel zooms around the pointer. Zoom is saved with the map; node positions and connection points remain editable at every scale.
- Export image offers PNG and standalone SVG. Both contain the whole map with its shapes, arrows, labels, and current theme colours. Export notes keeps an editable JSON backup of the map.

- Use a node's × button, or select nodes/connections and choose Delete selected. Deleting a node also removes its attached connections. Undo delete restores recent deletions during the current tab session.
- Hint shows a temporary guide for the selected block; Hide hints collapses it. Editing a hint turns it into your own content, so hiding hints keeps those edits. Answer confirms the authored concepts without overwriting edited node text.
- Click a shape to select it; drag its body to move it. Shift-click selects more shapes for moving together. Colour, shape, and size controls appear for the selection.
- Double-click a shape to edit its text. Enter saves, Shift+Enter adds a line, and Escape cancels. Add shape starts editing immediately; double-clicking empty canvas also adds a shape.
- Drag a blue point on a shape to a point on another shape to connect them. The arrow stays attached to those points when the shapes move. Escape or dropping on empty canvas cancels.
- Double-click a line or its label to type a relationship directly on the canvas. Enter or clicking elsewhere saves; Escape cancels. Select a connection and press Enter for keyboard editing.
- Grid and Left to right use spacing based on node size. The board scrolls when the map grows. Older automatic layouts are refreshed once using the corrected spacing; manual dragging switches to Free arrangement.
