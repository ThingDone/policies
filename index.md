# Opting Out of GitHub Copilot Model Training

**Last updated:** April 16, 2026
**Applies to:** Anyone with a personal GitHub account using Copilot Free, Pro, or Pro+

Starting **April 24, 2026**, GitHub began using interaction data from Copilot Free, Pro, and Pro+ users to train its AI models by default. This guide walks through every setting you should check to fully opt out.

> **Note:** If your Copilot seat is provided through a **Copilot Business or Enterprise** subscription (i.e., your company pays for it), your data is already contractually excluded from training. This guide is primarily for personal Copilot accounts — but even Business/Enterprise users should do a quick check since personal accounts you also own are handled separately.

---

## Step 1 — Disable model training on your GitHub account

This is the most important setting.

1. Sign in at **github.com**.
2. Click your profile picture in the upper-right corner → **Settings**.
3. In the left sidebar, scroll down and click **Copilot** → **Features**.
   - Direct link: `https://github.com/settings/copilot/features`
4. Scroll to the **Privacy** section.
5. Find **"Allow GitHub to use my data for AI model training"** and set the dropdown to **Disabled**.

> If you don't see this setting, you're likely signed into an account that already has a Copilot Business or Enterprise license, which means you're automatically excluded.

## Step 2 — Disable the older "product improvements" data collection

There is a separate, older toggle that predates the training policy and still allows data to be retained and shared with Microsoft. Disable it too.

1. Still on the **Copilot settings** page (`https://github.com/settings/copilot`).
2. Find **"Allow GitHub to use my code snippets from the code editor for product improvements"** and **uncheck** it.

## Step 3 — Block suggestions matching public code (optional but recommended)

This doesn't affect training, but it prevents Copilot from surfacing code that matches existing public repositories — useful for avoiding accidental copyright or licensing issues in your own code.

1. On the same **Copilot settings** page.
2. Next to **Suggestions matching public code**, set the dropdown to **Block**.

## Step 4 — Disable IDE telemetry

The settings above control what GitHub does on their end. Your IDE also sends telemetry that's worth turning off.

### VS Code

1. Open the Command Palette: `Cmd+Shift+P` (Mac) or `Ctrl+Shift+P` (Windows/Linux).
2. Type **Preferences: Open User Settings** and press Enter.
3. Search for `telemetry.telemetryLevel`.
4. Set it to **off**.

Alternatively, edit `settings.json` directly:
```json
"telemetry.telemetryLevel": "off"
```

### JetBrains IDEs (IntelliJ, PyCharm, WebStorm, etc.)

1. Open **Settings** → **Tools** → **GitHub Copilot**.
2. Uncheck **Send usage statistics** and any telemetry-related options.

### Neovim / Vim

Check your Copilot plugin configuration. For the official `github/copilot.vim` plugin, telemetry is tied to the GitHub account settings configured in Steps 1–2.

## Step 5 — Repeat for every personal GitHub account

If you have multiple GitHub accounts (personal, side project, etc.), **the setting is per-account**. Sign into each one and repeat Steps 1 and 2.

## Step 6 — Verify

After making these changes:

- Revisit `https://github.com/settings/copilot/features` and confirm the **"Allow GitHub to use my data for AI model training"** dropdown still reads **Disabled**.
- Check that the older product improvements checkbox is still unchecked.

GitHub has stated that previously-saved opt-outs are preserved, but it doesn't hurt to confirm — especially after major policy updates.

---

## FAQ

**Q: I'm on Copilot Business. Do I need to do this?**
No. Copilot Business and Enterprise customers are contractually excluded from training data collection, regardless of individual settings.

**Q: I use Copilot through my employer, but I also have a personal GitHub account. Am I at risk?**
If you only ever use Copilot while signed in to the account that holds the Business/Enterprise license, you're covered. The risk is using Copilot on a personal account that happens to be working in your employer's codebase. Per GitHub's FAQ, being a **member or outside collaborator** of a paid organization also excludes your interaction data from training — but only for the time you're actually a member. If you leave the org, the exclusion ends.

**Q: Does opting out affect the quality of my Copilot suggestions?**
GitHub states that opting out does not reduce feature access. You still get the full Copilot experience.

**Q: Does this apply retroactively to data already collected?**
GitHub hasn't publicly committed to deleting historical data. The opt-out applies going forward.

**Q: What about Copilot CLI?**
Copilot CLI respects the same account-level opt-out as VS Code and other IDEs. Steps 1–2 cover it.

**Q: Private repository code — is any of it safe from training if I don't opt out?**
Only if you never open those repositories while Copilot is active. While Copilot is running in a private repo, code snippets can be sent to GitHub as part of the interaction and may be used for training unless you've opted out. GitHub does not pull private repository contents "at rest."

---

## Sources

- [Updates to GitHub Copilot interaction data usage policy (GitHub Blog, March 2026)](https://github.blog/news-insights/company-news/updates-to-github-copilot-interaction-data-usage-policy/)
- [FAQ: Privacy Statement update on Copilot data use for model training](https://github.com/orgs/community/discussions/188488)
- [Managing GitHub Copilot policies as an individual subscriber (GitHub Docs)](https://docs.github.com/copilot/how-tos/manage-your-account/managing-copilot-policies-as-an-individual-subscriber)
