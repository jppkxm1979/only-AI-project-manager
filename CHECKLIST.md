# CHECKLIST.md

## only-AI-project-manager setup

### 1. GitHub App or fallback token

Preferred:

- variable `GUARDIAN_APP_CLIENT_ID`
- secret `GUARDIAN_APP_PRIVATE_KEY`

Fallback:

- secret `TARGET_REPO_TOKEN`

### 2. Test guardian

Repository: `only-AI-project-manager`

1. `Actions`
2. `Guardian Monitor`
3. `Run workflow`
4. Confirm summary shows:
   - `Auth mode: github_app` or `fallback_token`

### 3. Confirm report issue

1. Open `Issues`
2. Look for `Guardian Stability Report`
3. Confirm it is created or updated after a run
