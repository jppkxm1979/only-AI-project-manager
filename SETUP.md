# SETUP.md

`only-AI-project-manager` must be able to act on `jppkxm1979/only-AI-project`.

Best option: GitHub App  
Fallback option: fine-grained personal access token

## Option A: GitHub App

### 1. Create the app

On GitHub:

1. Go to `Settings` for your account.
2. Open `Developer settings`.
3. Open `GitHub Apps`.
4. Click `New GitHub App`.

Recommended values:

- App name: `only-ai-project-guardian`
- Homepage URL: your GitHub profile or the manager repo URL
- Webhook: off for now

Repository permissions to grant:

- `Actions`: `Read and write`
- `Contents`: `Read and write`
- `Pull requests`: `Read and write`
- `Issues`: `Read and write`
- `Metadata`: `Read-only`

Install the app only on:

- `only-AI-project`
- optionally `only-AI-project-manager`

### 2. Generate the private key

Inside the GitHub App page:

1. Open the app
2. Scroll to `Private keys`
3. Click `Generate a private key`
4. A `.pem` file will download

### 3. Add manager repo variable and secret

In `only-AI-project-manager`:

1. Open `Settings`
2. Open `Secrets and variables` -> `Actions`
3. In `Variables`, create:
   - `GUARDIAN_APP_CLIENT_ID`
4. In `Secrets`, create:
   - `GUARDIAN_APP_PRIVATE_KEY`

For `GUARDIAN_APP_CLIENT_ID`, copy the App `Client ID` from the GitHub App page.

For `GUARDIAN_APP_PRIVATE_KEY`, paste the full PEM text including:

```text
-----BEGIN RSA PRIVATE KEY-----
...
-----END RSA PRIVATE KEY-----
```

### 4. Test it

In `only-AI-project-manager`:

1. Open `Actions`
2. Open `Guardian Monitor`
3. Click `Run workflow`

Expected result:

- auth mode becomes `github_app`
- target workflows in `only-AI-project` can be monitored and re-enabled

## Option B: Fine-Grained Token Fallback

Use this only if the GitHub App path is inconvenient.

### 1. Create token

1. Click your avatar
2. Open `Settings`
3. Open `Developer settings`
4. Open `Personal access tokens`
5. Open `Fine-grained tokens`
6. Click `Generate new token`

Set:

- Resource owner: your account
- Repository access: `Only select repositories`
- Selected repository: `only-AI-project`

Grant repository permissions:

- `Actions`: `Read and write`
- `Contents`: `Read and write`
- `Pull requests`: `Read and write`
- `Issues`: `Read and write`
- `Metadata`: `Read-only`

Then create the token and copy it once.

### 2. Add secret

In `only-AI-project-manager`:

1. Open `Settings`
2. Open `Secrets and variables` -> `Actions`
3. Create repository secret:
   - `TARGET_REPO_TOKEN`

### 3. Test it

Run `Guardian Monitor` manually.

Expected result:

- auth mode becomes `fallback_token`

## Recommended Target Repo Settings

In `only-AI-project`:

1. Add repository secret:
   - `GEMINI_API_KEY`
2. Protect `main`
3. Require pull requests before merging
4. Require status checks to pass
5. Require `Autonomous Verify / verify`
6. In Actions settings, allow workflows to create pull requests if needed

## Which one should you choose?

- Choose `GitHub App` if you want the safer long-term setup
- Choose `TARGET_REPO_TOKEN` if you want the fastest path today
