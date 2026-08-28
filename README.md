# secrets-scanner-canary

This is a **deliberately seeded test repository** for end-to-end validation of
the [secrets-scanner](https://github.com/) GitHub New-Repo Secret Scanner
pipeline (GH Archive reader → watchlist filters → clone → scan → findings DB).

It intentionally contains a `.env` file with **fake, non-functional,
officially-documented example credentials** (AWS `AKIAIOSFODNN7EXAMPLE`,
Stripe's own published test key, GitHub's own published PAT-format example,
etc. — none of these are real, active, or capable of accessing anything).
They exist only so the scanner's regex patterns have something real to
match against on a live public GitHub repository, without risking any real
resource.

This repository is periodically touched (small commit) so that its
`PushEvent`s appear in the live [GH Archive](https://www.gharchive.org/)
stream, letting us verify the pipeline end-to-end against real data (not
just fixtures) without waiting for an organic secret leak to show up.

Do not report these as real leaked secrets — they are canary/test values.
