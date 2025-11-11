# Repository Migration Guide

This guide walks you through migrating the Weather MCP project to the GitHub organization with separate repositories.

## Overview

**Goal:** Transition from a single repository (`dgahagan/weather-mcp`) to four independent repositories under the `weather-mcp` organization.

**Repositories:**
- `weather-mcp/weather-mcp` (existing repo, transferred) - MCP server
- `weather-mcp/analytics-server` (new repo) - Analytics backend
- `weather-mcp/website` (new repo) - Public website and dashboard
- `weather-mcp/.github` (new repo) - Organization profile and shared docs

---

## Prerequisites

- [x] GitHub organization created: [weather-mcp](https://github.com/weather-mcp)
- [x] Write access to the organization
- [x] Git installed locally
- [x] GitHub CLI: `gh` command (recommended and used)

---

## Phase 1: Transfer MCP Server Repository ✅ COMPLETED

> **Status:** Completed - Repository transferred to `weather-mcp/weather-mcp`

### Step 1: Transfer Repository on GitHub

1. **Go to the repository settings:**
   - Navigate to: https://github.com/dgahagan/weather-mcp/settings

2. **Scroll to "Danger Zone"**

3. **Click "Transfer ownership"**

4. **Fill in the transfer form:**
   - New owner: `weather-mcp`
   - New repository name: `mcp-server`
   - Type the repository name to confirm: `dgahagan/weather-mcp`

5. **Click "I understand, transfer this repository"**

### Step 2: Update Local Git Remote

```bash
cd /home/dgahagan/work/personal/weather-mcp/weather-mcp

# Verify current remote
git remote -v

# Update to new organization URL
git remote set-url origin git@github.com:weather-mcp/mcp-server.git

# Verify the change
git remote -v

# Fetch to confirm connection
git fetch origin
```

### Step 3: Update Local Branch Tracking (if needed)

```bash
# If your main branch isn't tracking correctly
git branch --set-upstream-to=origin/main main

# Or if you use master
git branch --set-upstream-to=origin/master master
```

### Step 4: Verify Transfer

```bash
# Check that you can pull
git pull

# Check repository status
git status
```

**✅ Checkpoint:** The MCP server repository should now be at `github.com/weather-mcp/mcp-server` and your local repo should be connected to it.

---

## Phase 2: Create Analytics Server Repository ✅ COMPLETED

> **Status:** Completed - Repository created at `weather-mcp/analytics-server` using gh CLI

### Step 1: Initialize Git Repository Locally

```bash
cd /home/dgahagan/work/personal/weather-mcp/analytics-server

# Initialize git
git init

# Set default branch to main (if not already set globally)
git branch -M main

# Check git status
git status
```

### Step 2: Create .gitignore (if not exists)

The `.gitignore` file has already been created. Verify it's present:

```bash
cat .gitignore
```

It should include:
- `node_modules/`
- `.env` and `.env.local`
- `dist/`
- `coverage/`
- Other common exclusions

### Step 3: Create Initial Commit

```bash
# Stage all files
git add .

# Create initial commit with a descriptive message
git commit -m "Initial analytics server structure

- Project structure with src/, tests/, scripts/
- Package.json with Fastify, PostgreSQL, Redis dependencies
- TypeScript configuration
- Comprehensive implementation plan (ANALYTICS_SERVER_PLAN.md)
- README with setup instructions and architecture overview
- .gitignore for Node.js projects

This commit establishes the foundation for the privacy-first
analytics collection server for Weather MCP.

🤖 Generated with Claude Code
Co-Authored-By: Claude <noreply@anthropic.com>"

# Verify commit
git log --oneline
```

### Step 4: Create GitHub Repository

**Option A: Using GitHub Web Interface**

1. Go to: https://github.com/organizations/weather-mcp/repositories/new

2. Fill in the details:
   - **Repository name:** `analytics-server`
   - **Description:** `Privacy-first analytics collection server for Weather MCP`
   - **Visibility:** Public
   - **DO NOT** initialize with README, .gitignore, or license (we already have these)

3. Click **"Create repository"**

**Option B: Using GitHub CLI (faster)**

```bash
# Create repository using gh CLI
gh repo create weather-mcp/analytics-server \
  --public \
  --description "Privacy-first analytics collection server for Weather MCP" \
  --source=. \
  --remote=origin \
  --push

# This creates the repo, adds remote, and pushes in one command!
```

**Option C: Manual remote setup (if repo already created)**

```bash
# Add remote
git remote add origin git@github.com:weather-mcp/analytics-server.git

# Push to GitHub
git push -u origin main
```

### Step 5: Configure Repository Settings

On GitHub (https://github.com/weather-mcp/analytics-server):

1. **About section:**
   - Add description: "Privacy-first analytics collection server for Weather MCP"
   - Add website: https://weather-mcp.dev
   - Add topics: `analytics`, `privacy`, `postgresql`, `timescaledb`, `fastify`, `redis`, `weather-mcp`

2. **Settings → Features:**
   - ✅ Issues
   - ✅ Discussions (optional, recommended)
   - ☐ Projects (optional)
   - ☐ Wiki (not needed yet)

3. **Settings → Branches:**
   - Set default branch to `main` (if not already)
   - Consider adding branch protection rules (optional for now)

**✅ Checkpoint:** The analytics-server repository should now be at `github.com/weather-mcp/analytics-server` with all files pushed.

---

## Phase 3: Create Website Repository ✅ COMPLETED

> **Status:** Completed - Repository created at `weather-mcp/website` using gh CLI

### Step 1: Initialize Git Repository Locally

```bash
cd /home/dgahagan/work/personal/weather-mcp/website

# Initialize git
git init

# Set default branch to main
git branch -M main

# Check status
git status
```

### Step 2: Verify .gitignore

The `.gitignore` file has already been created. Verify:

```bash
cat .gitignore
```

It should include:
- `node_modules/`
- `.next/`
- `.env*.local`
- Other Next.js-specific exclusions

### Step 3: Create Initial Commit

```bash
# Stage all files
git add .

# Create initial commit
git commit -m "Initial website structure

- Next.js 14 project structure with App Router
- Package.json with Next.js, React, Tailwind CSS, Recharts
- TypeScript configuration
- next.config.js with security headers and optimization
- Comprehensive implementation plan (WEBSITE_IMPLEMENTATION_PLAN.md)
- README with development guide and architecture overview
- .gitignore for Next.js projects

This commit establishes the foundation for the public website
and analytics dashboard at weather-mcp.dev.

🤖 Generated with Claude Code
Co-Authored-By: Claude <noreply@anthropic.com>"

# Verify commit
git log --oneline
```

### Step 4: Create GitHub Repository

**Option A: Using GitHub Web Interface**

1. Go to: https://github.com/organizations/weather-mcp/repositories/new

2. Fill in the details:
   - **Repository name:** `website`
   - **Description:** `Public website and analytics dashboard for Weather MCP (weather-mcp.dev)`
   - **Visibility:** Public
   - **DO NOT** initialize with README, .gitignore, or license

3. Click **"Create repository"**

**Option B: Using GitHub CLI**

```bash
# Create repository using gh CLI
gh repo create weather-mcp/website \
  --public \
  --description "Public website and analytics dashboard for Weather MCP (weather-mcp.dev)" \
  --source=. \
  --remote=origin \
  --push
```

**Option C: Manual remote setup**

```bash
# Add remote
git remote add origin git@github.com:weather-mcp/website.git

# Push to GitHub
git push -u origin main
```

### Step 5: Configure Repository Settings

On GitHub (https://github.com/weather-mcp/website):

1. **About section:**
   - Add description: "Public website and analytics dashboard for Weather MCP (weather-mcp.dev)"
   - Add website: https://weather-mcp.dev
   - Add topics: `nextjs`, `react`, `dashboard`, `analytics`, `weather`, `tailwindcss`, `typescript`, `weather-mcp`

2. **Settings → Features:**
   - ✅ Issues
   - ✅ Discussions (optional)
   - ☐ Projects (optional)

3. **Settings → Pages (when ready to deploy):**
   - Configure GitHub Pages or connect to Vercel

**✅ Checkpoint:** The website repository should now be at `github.com/weather-mcp/website` with all files pushed.

---

## Phase 4: Create Organization Profile ✅ COMPLETED

> **Status:** Completed - Created `.github` repo in workspace using gh CLI

This special repository displays on the organization profile page at https://github.com/weather-mcp.

### Implementation Notes

We streamlined this phase by:
1. Using `gh` CLI to create and clone in one command
2. Creating the `.github` folder directly in the workspace alongside other repos
3. Adding organization documentation (profile README and migration guide)

### Step 1: Create and Clone .github Repository

**Using GitHub CLI (Streamlined Approach):**

```bash
cd /home/dgahagan/work/personal/weather-mcp

# Create repo and clone it in one command
gh repo create weather-mcp/.github \
  --public \
  --description "Organization profile and shared resources" \
  --clone

# This creates:
# - Repository at github.com/weather-mcp/.github
# - Local folder at .github/ in your workspace
```

### Step 2: Add Organization Profile README

```bash
cd .github

# Create profile directory and add README
mkdir -p profile
cp ../docs/ORGANIZATION_PROFILE_README.md ./profile/README.md

# Set branch to main and commit
git branch -M main
git add profile/README.md
git commit -m "Add organization profile README

- Project overview and feature highlights
- Links to all repositories
- Quick start guide
- Community resources
- Contributing guidelines
- Live stats and badges

🤖 Generated with Claude Code
Co-Authored-By: Claude <noreply@anthropic.com>"

git push -u origin main
```

### Step 3: Add Organization Documentation

```bash
# Add migration guide to .github repo
mkdir -p docs
cp ../docs/REPOSITORY_MIGRATION_GUIDE.md ./docs/

git add docs/
git commit -m "Add organization documentation"
git push
```

### Step 4: Update Workspace Structure

After creating `.github` repo, update workspace `.gitignore`:

```bash
cd /home/dgahagan/work/personal/weather-mcp

# Update .gitignore to include .github/ folder
echo ".github/" >> .gitignore
```

Final workspace structure:
```
weather-mcp/                    (workspace - NO git)
├── weather-mcp/               → github.com/weather-mcp/weather-mcp
├── analytics-server/          → github.com/weather-mcp/analytics-server
├── website/                   → github.com/weather-mcp/website
├── .github/                   → github.com/weather-mcp/.github
├── .gitignore                 (protects workspace)
└── README.md                  (local workspace guide)
```

### Step 5: Add Organization Description (Optional)

On GitHub, you can optionally add more organization metadata:

1. Go to: https://github.com/settings/organizations
2. Select `weather-mcp`
3. Add profile:
   - **Name:** Weather MCP
   - **Display name:** Weather MCP
   - **Description:** "Open-source weather data ecosystem for Claude Desktop"
   - **Email:** (your email)
   - **Website:** https://weather-mcp.dev
   - **Twitter:** @weather_mcp (if you have one)

**✅ Checkpoint:** The organization profile at https://github.com/weather-mcp now displays the profile README and all project links!

---

## Phase 5: Update Cross-Repository References

### Step 1: Verify All URL Updates

The following files have been automatically updated:

**MCP Server Repository:**
- ✅ `package.json` - repository URLs
- ✅ `smithery.yaml` - homepage and repository
- ✅ `README.md` - GitHub badges and links
- ✅ `SECURITY.md` - issue reporting URLs
- ✅ `CLAUDE.md` - documentation links
- ✅ All files in `docs/` directory

**Analytics Server:**
- ✅ `README.md` - links to other repos

**Website:**
- ✅ `README.md` - links to other repos

**Root Workspace:**
- ✅ `README.md` - updated with new repo structure

### Step 2: Test All Links

Manually verify key links work:

- [ ] https://github.com/weather-mcp
- [ ] https://github.com/weather-mcp/mcp-server
- [ ] https://github.com/weather-mcp/analytics-server
- [ ] https://github.com/weather-mcp/website
- [ ] https://github.com/weather-mcp/.github
- [ ] Old URL redirects: https://github.com/dgahagan/weather-mcp → new URL

---

## Phase 6: Update External Services

### Services to Update

1. **npm Package (if published):**
   ```bash
   # After transferring, republish with updated package.json
   cd /home/dgahagan/work/personal/weather-mcp/weather-mcp
   npm publish
   ```

2. **Smithery Registry:**
   - Update at: https://smithery.ai/dashboard
   - New repository URL: `https://github.com/weather-mcp/mcp-server`

3. **GitHub Actions Secrets:**
   - Go to each repository's Settings → Secrets and variables → Actions
   - Re-add any secrets that didn't transfer:
     - `NOAA_USER_AGENT` (if used in CI)
     - Any other API tokens or credentials

4. **Badges and Shields:**
   - GitHub badges will automatically update
   - Custom badges may need URL updates

5. **External Documentation:**
   - Update any external links or documentation
   - Check if you've mentioned the repo URL anywhere else

---

## Phase 7: Announce Migration

### Update README Badges

Ensure all repos have correct badges:

**MCP Server:**
```markdown
[![GitHub Stars](https://img.shields.io/github/stars/weather-mcp/mcp-server?style=social)](https://github.com/weather-mcp/mcp-server)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![npm version](https://img.shields.io/npm/v/@dangahagan/weather-mcp)](https://www.npmjs.com/package/@dangahagan/weather-mcp)
```

### Create Announcement (Optional)

Consider creating a discussion or issue announcing the migration:

**Title:** "🎉 Weather MCP has moved to an organization!"

**Body:**
```markdown
## Weather MCP is now an organization! 🎊

We're excited to announce that Weather MCP has transitioned to a GitHub organization to better support our growing ecosystem.

### What's Changed?

**Old:** `github.com/dgahagan/weather-mcp`
**New:** `github.com/weather-mcp/mcp-server`

### Three Repositories

We've also split the project into three focused repositories:

1. **[MCP Server](https://github.com/weather-mcp/mcp-server)** - Core weather data server (v1.6.1)
2. **[Analytics Server](https://github.com/weather-mcp/analytics-server)** - Privacy-first analytics (Coming Soon)
3. **[Website](https://github.com/weather-mcp/website)** - Public website and dashboard (Coming Soon)

### For Users

- **Nothing changes!** The npm package still works the same way
- **Old URLs redirect** - All existing links will continue to work
- **Issues and PRs** - All preserved and transferred

### For Contributors

- **More focused repos** - Contribute to the specific area you're interested in
- **Independent releases** - Each project can evolve at its own pace
- **Better organization** - Clearer structure for the ecosystem

Visit our new organization: https://github.com/weather-mcp

Thanks for being part of the Weather MCP community! ☀️
```

---

## Verification Checklist

Before considering the migration complete, verify:

### MCP Server Repository
- [x] Repository transferred to `weather-mcp/weather-mcp`
- [x] Local git remote updated
- [x] Can push and pull successfully
- [ ] All URLs in code/docs updated (Phase 5)
- [ ] GitHub Actions still working (if any) (Phase 5)
- [ ] npm package links work (Phase 6)

### Analytics Server Repository
- [x] Repository created at `weather-mcp/analytics-server`
- [x] Initial commit pushed
- [x] Repository settings configured
- [x] Topics and description added
- [x] README displays correctly

### Website Repository
- [x] Repository created at `weather-mcp/website`
- [x] Initial commit pushed
- [x] Repository settings configured
- [x] Topics and description added
- [x] README displays correctly

### Organization Profile
- [x] `.github` repository created
- [x] Organization README displays at https://github.com/weather-mcp
- [x] Migration guide added to `.github/docs/`
- [x] Workspace structure updated with `.github/` folder
- [ ] Organization description set (optional)
- [x] Links to all repos work

### External Services
- [ ] npm package updated (if published) (Phase 6)
- [ ] Smithery registry updated (if registered) (Phase 6)
- [ ] GitHub Actions secrets re-added (Phase 6)
- [ ] Old URLs redirect correctly (verify in Phase 5)

---

## Rollback Plan

If something goes wrong, here's how to rollback:

### For Repository Transfer

1. **Transfer can be reversed:**
   - Go to `weather-mcp/mcp-server` settings
   - Transfer back to `dgahagan` account
   - Rename back to `weather-mcp`

2. **Local git remote:**
   ```bash
   git remote set-url origin git@github.com:dgahagan/weather-mcp.git
   ```

### For New Repositories

1. **Delete the repositories:**
   - Go to repository settings
   - Scroll to "Danger Zone"
   - Click "Delete this repository"

2. **No local changes needed** (they're separate directories)

---

## Troubleshooting

### Issue: "Permission denied" when pushing

**Solution:**
```bash
# Verify SSH key is added to GitHub
ssh -T git@github.com

# Or use HTTPS instead
git remote set-url origin https://github.com/weather-mcp/mcp-server.git
```

### Issue: "Repository not found"

**Solution:**
```bash
# Verify remote URL
git remote -v

# Update if wrong
git remote set-url origin git@github.com:weather-mcp/mcp-server.git
```

### Issue: "Refusing to merge unrelated histories"

**Solution:**
```bash
# Allow unrelated histories (rare, only if force-creating new repo)
git pull origin main --allow-unrelated-histories
```

### Issue: Transfer takes a long time

**Expected:** Transfers usually complete in 30 seconds to 2 minutes. If it takes longer, check your network connection or contact GitHub Support.

---

## Post-Migration Tasks

After migration is complete:

1. **Update your local bookmarks** to new GitHub URLs

2. **Share the news:**
   - Twitter/social media announcement
   - Update your personal README or portfolio
   - Notify any collaborators

3. **Monitor for issues:**
   - Check GitHub Issues for any migration-related problems
   - Monitor CI/CD pipelines
   - Verify external integrations

4. **Clean up (after 30 days):**
   - GitHub redirects last ~1 year
   - After verifying everything works, can consider archiving old references

---

## Success! 🎉

Once all checkboxes are complete:

- ✅ Three separate repositories created
- ✅ Organization profile looks great
- ✅ All cross-references updated
- ✅ External services configured

**Your Weather MCP organization is now ready to grow!**

Visit: https://github.com/weather-mcp

---

## Getting Help

If you encounter issues:

1. **Check GitHub's transfer documentation:**
   - https://docs.github.com/en/repositories/creating-and-managing-repositories/transferring-a-repository

2. **Search GitHub Issues:**
   - Often others have encountered similar problems

3. **Ask in Discussions:**
   - https://github.com/weather-mcp/mcp-server/discussions

4. **Contact GitHub Support:**
   - If transfer is stuck or having technical issues

---

## Migration Progress

**✅ Phases 1-4 Completed!**

- ✅ Phase 1: MCP Server Repository transferred to `weather-mcp/weather-mcp`
- ✅ Phase 2: Analytics Server Repository created
- ✅ Phase 3: Website Repository created
- ✅ Phase 4: Organization Profile created (`.github` repo)
- ⏳ Phase 5: Update Cross-Repository References (next)
- ⏳ Phase 6: Update External Services
- ⏳ Phase 7: Announce Migration

---

**Last Updated:** 2025-11-11
**Document Version:** 1.1 (Updated with completion status)
