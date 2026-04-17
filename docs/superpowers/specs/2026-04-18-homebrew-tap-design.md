# Homebrew Tap for BeaversLab

## Overview

Create a public Homebrew tap repository `BeaversLab/homebrew-tap` to distribute waylog and future BeaversLab CLI tools via `brew`.

## Repository

- **Name**: `homebrew-tap`
- **Full path**: `BeaversLab/homebrew-tap`
- **Visibility**: public
- **Local path**: `/Users/marco/Documents/git/github.com/BeaversLab/homebrew-tap`

## Structure

```
homebrew-tap/
├── Formula/
│   └── waylog.rb
├── README.md
└── .gitignore
```

## Formula: waylog.rb

Downloads the macOS universal binary from GitHub Releases.

```ruby
class Waylog < Formula
  desc "Automatically save chats from Claude, Codex, and Gemini CLI to local Markdown files."
  homepage "https://github.com/BeaversLab/waylog-cli"
  url "<release-url>"
  sha256 "<sha256>"
  version "<version>"
  license "Apache-2.0"

  def install
    bin.install "waylog"
  end

  test do
    system "#{bin}/waylog", "--version"
  end
end
```

The actual URL, SHA256, and version are populated automatically by the waylog-cli release workflow.

## Integration with waylog-cli Release Workflow

The existing `update-formula` job in `.github/workflows/release.yml` handles:

1. Downloads macOS universal binary from the draft release
2. Calculates SHA256
3. Writes `Formula/waylog.rb` with correct values
4. Commits and pushes to `BeaversLab/homebrew-tap`

No changes needed to the release workflow.

## Token Setup

A GitHub PAT with `repo` scope must be configured as `HOMEBREW_TAP_TOKEN` in the `BeaversLab/waylog-cli` repository secrets. This allows the release workflow to push to the tap repository.

## Installation (end user)

```bash
brew tap beaverslab/tap
brew install waylog
```

## Future

The tap is generic — additional formulas for other BeaversLab tools (crawfish, dam, etc.) can be added under `Formula/` at any time.
