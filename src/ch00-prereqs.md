# Pre-requisites: Pick One Track

- Explain why the AI Engineer roadmap starts with traditional software engineering instead of AI.
- Compare the Frontend, Backend, and Full-Stack tracks and pick the one that fits your goal.
- List the minimum exit skills for your chosen track before starting ch01.
- Run the environment self-check and close any gaps in your setup.

## Detailed notes

The roadmap opens with a node called `Pre-requisites (One of these)`. It links to three separate
roadmaps — Frontend, Backend, Full-Stack — and the parenthetical is the whole point: you complete
exactly one of them, not all three. AI engineering is applied work. Every later chapter assumes you
can already build ordinary software: run code from a terminal, install packages, call an HTTP API,
read an error traceback, and commit to git. None of the chapters teach those from zero.

Pick the track that matches what you want to build first. If you want chat interfaces and streaming
UIs, pick Frontend. If you want API servers that call models and store results, pick Backend. If
you want to ship complete products alone, pick Full-Stack. There is no best track. There is only
the track whose exit skills match the chapters you care about most.

### Frontend

The [Frontend roadmap](https://roadmap.sh/frontend) covers HTML for page structure, CSS for
styling and layout, and JavaScript for behavior in the browser, followed by one framework and the
tooling around it (package manager, bundler, version control). For AI engineering, the parts that
pay off earliest are JavaScript fluency and HTTP: fetching from APIs, handling async responses with
`async`/`await`, and rendering streamed text token by token. Those map directly to ch04 (streaming
responses) and ch12 (multimodal apps with browser-side inference via Transformers.js).

You are ready to move on when you can build a single-page app that calls a public JSON API,
renders the response, handles loading and error states, and is committed to a git repository. You
do not need CSS mastery, animations, or three frameworks. One framework, one deployed page, solid
async fundamentals.

### Backend

The [Backend roadmap](https://roadmap.sh/backend) covers a server-side language, HTTP and REST
APIs, databases, authentication basics, and deployment. For this book, do the backend track in
Python. Every code example from ch03 onward runs in Python, and the AI ecosystem — the OpenAI SDK,
LangChain, LlamaIndex, Chroma, sentence-transformers — is Python-first. Learning backend in another
language means translating every example before you can run it.

You are ready to move on when you can build a small HTTP API in Python (FastAPI or Flask) that
reads input, calls another service over the network, stores something in a database, returns JSON,
and runs from a virtual environment with its dependencies pinned. That is the exact shape of every
RAG server in ch09 and every agent server in ch10, with an LLM call in the middle.

### Full-Stack

The [Full-Stack roadmap](https://roadmap.sh/full-stack) covers both ends plus the glue: frontend,
a backend language, databases, and deploying a complete application. Pick this track if your goal
is shipping products, which is also the goal of ch13. It takes longer than either single track, and
that is the trade. You finish able to build the chat UI, the API behind it, and the deployment that
serves both.

You are ready to move on when you have one deployed application with a frontend that talks to your
own backend over HTTP, backed by a database. Deployment counts: an app that only runs on localhost
has not taught you the environment variables, build steps, and logs that break every first AI app
launch.

## How it works

The prerequisite works as a filter for everything after it. Each chapter consumes specific baseline
skills and fails in a specific way without them:

- ch03 (OpenAI API) assumes you can make authenticated HTTP requests and parse JSON. Without
  backend basics, every 401 and rate-limit error looks like a model problem instead of a request
  problem.
- ch04 (streaming) assumes async handling. Without it, streamed tokens pile up in a buffer and the
  UI updates once at the end, defeating the purpose.
- ch07–ch09 (embeddings, vector DBs, RAG) assume local Python environments and dependency
  management. Without them, version conflicts between `numpy`, `torch`, and client libraries eat
  days.
- ch13 (shipping) assumes git and deployment. Without them, a working notebook never becomes a URL
  anyone else can open.

Tokens, cost, and limits do not apply to this chapter. The cost here is time: calibrate it by
working through your chosen track's roadmap checklist item by item instead of estimating weeks.

## Example (Python)

Stdlib only — requires Python >= 3.10. Save as `prereq_check.py` and run `python3 prereq_check.py`.
It verifies the baseline this book assumes: a new-enough interpreter, `pip`, `git`, and a working
virtual environment. Fix every `[FAIL]` before starting ch01.

```python
# prereq_check.py — stdlib only, Python >= 3.10. Run: python3 prereq_check.py
import shutil
import subprocess
import sys
import tempfile
import venv

PASS, FAIL = "[PASS]", "[FAIL]"
failures = 0


def check(name, ok, hint=""):
    global failures
    print(f"{PASS if ok else FAIL} {name}" + ("" if ok else f" — {hint}"))
    if not ok:
        failures += 1


def run(*args, timeout=60):
    return subprocess.run(list(args), capture_output=True, text=True, timeout=timeout)


check(
    f"python >= 3.10 (found {sys.version.split()[0]})",
    sys.version_info >= (3, 10),
    "install Python 3.10+ from python.org or your package manager",
)
pip_probe = run(sys.executable, "-m", "pip", "--version")
check(
    f"pip for this interpreter ({pip_probe.stdout.strip().split()[1] if pip_probe.returncode == 0 else 'missing'})",
    pip_probe.returncode == 0,
    "reinstall Python with pip included",
)
check(
    "git available",
    shutil.which("git") is not None,
    "install git from git-scm.com and set user.name / user.email",
)

with tempfile.TemporaryDirectory() as tmp:
    env_dir = f"{tmp}/venv"
    try:
        venv.create(env_dir, with_pip=True)
        pip_bin = f"{env_dir}/bin/pip" if sys.platform != "win32" else f"{env_dir}\\Scripts\\pip.exe"
        r = subprocess.run([pip_bin, "--version"], capture_output=True, text=True, timeout=60)
        check("virtual environment with pip works", r.returncode == 0, r.stderr.strip()[-200:])
    except Exception as e:  # noqa: BLE001 — report any venv failure as a failed check
        check("virtual environment with pip works", False, str(e)[-200:])

print(f"\n{failures} failing check(s). Fix all [FAIL] lines, then start ch01.")
sys.exit(1 if failures else 0)
```

## Pitfalls / Gotchas

- Studying all three tracks. The node says one of these. Frontend plus backend plus full-stack is
  a year of prerequisites for a book you could have started in weeks.
- Learning a framework before the fundamentals. React cannot teach you `async`/`await`, and
  FastAPI cannot teach you HTTP. Chapters 3 and 4 punish exactly those gaps.
- Doing the backend track in another language. Every example in this book is Python. Node, Go, or
  Java backends are fine careers and add a translation step to every chapter here.
- Passive tutorials with no deployed artifact. If nothing you built is running somewhere other
  than your laptop, the exit criteria above are not met.
- Python 2 vs 3. Some systems still ship a `python` binary that is Python 2. Always invoke
  `python3`, and confirm with the check script.
- Skipping git and the terminal. AI code editors (ch13) generate code fast, but the generated
  project still needs committing, running, and debugging by you.

## Free resources

- [Frontend Roadmap](https://roadmap.sh/frontend) — the track checklist itself; work it top to bottom.
- [Backend Roadmap](https://roadmap.sh/backend) — the track checklist itself; do it in Python.
- [Full-Stack Roadmap](https://roadmap.sh/full-stack) — the track checklist itself; finish with one deployed app.
- [MDN Learn web development](https://developer.mozilla.org/en-US/docs/Learn_web_development) — reference docs for HTML, CSS, and JavaScript when the frontend track needs depth.
- [freeCodeCamp core curriculum](https://www.freecodecamp.org/learn) — free interactive exercises for the frontend track.
- [The Python Tutorial](https://docs.python.org/3/tutorial/) — the official language tour; covers everything the backend track assumes.
- [The Odin Project](https://www.theodinproject.com/) — free full-stack path with projects instead of videos.

## Done checklist

- [x] Can state why the roadmap requires one prior track and which one I picked
- [x] Meet the exit criteria of my chosen track (app, API, or deployed full-stack app in git)
- [x] `python3 prereq_check.py` passes with zero failures
- [x] `mdbook build` passes with this chapter included
