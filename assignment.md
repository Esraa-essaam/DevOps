# Assignment: Advanced Git & CI/CD Challenge

## Deliverables
Write a short technical guide addressing the team to solve these problems. For each section, provide clear explanations and the exact Git/YAML code needed.

### 1. Workflow Architecture & Protection
**Your Task:** Recommend a branching strategy to stop everyone from pushing directly to main.
* **Explain:** Choose either GitFlow or Trunk-Based Development. Briefly explain to the team why your choice is better for a fast-moving startup.
* **Action:** List at least two GitHub Branch Protection Rules you will enforce on the main branch to prevent bad code from being merged.

### 2. History Cleanup (Interactive Rebase)
**Your Task:** Teach the developers how to clean up their messy commits before asking for a code review.
* **Explain:** Describe the difference between the `pick` and `squash` commands during an interactive rebase.
* **Action:** Provide the exact command a developer should run to open an interactive rebase for their last 5 commits (`wip1`, `wip2`, `wip3`, `typo`, `done`).

### 3. The Emergency Surgery (Cherry-Picking)
**Your Task:** A critical bug is crashing the production servers right now! A developer fixed the bug, but accidentally committed the fix (commit hash: `8f3a9b2`) to the develop branch, which is currently full of broken code.
* **Explain:** Briefly explain what `git cherry-pick` does and why it is the perfect tool for this emergency.
* **Action:** Write the exact sequence of Git commands required to switch to the main branch, grab that specific fix, and push it to production safely.

### 4. Integration Testing with Docker Compose (GitHub Actions)
**Your Task:** To ensure code quality, we must prove our multi-container application actually works before it is merged into the `main` branch. 
* **Explain:** Why should integration tests be run against a Docker Compose stack in a CI pipeline rather than testing locally?
* **Action:** Write a complete GitHub Actions workflow file (`.github/workflows/compose-test.yml`) that accomplishes the following:
  1. Triggers automatically when a `pull_request` is opened against the `main` branch.
  2. Runs on an `ubuntu-latest` environment.
  3. Checks out the repository code.
  4. Starts a Docker Compose stack in detached mode (`docker-compose up -d`).
  5. Pauses for 15 seconds to allow the database and web server to fully initialize.
  6. Runs a network test (`curl -f http://localhost:8080 || exit 1`) to verify the web service is responding.
  7. Ensures the Docker Compose stack is torn down (`docker-compose down`) and logs are shown even if the network test fails.

---

**Submission Format:**
Submit your completed assignment as a single Markdown (`.md`) file or PDF. Be sure to use code blocks (`` ` ``) for all Git commands and YAML configurations to make it easy to read!
