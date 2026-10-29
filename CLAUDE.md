# Notes for Claude

## After a PR merges: run the content smoke checks

Every merge to `master` deploys the live site (`.github/workflows/deploy.yml`, GitHub Pages).
After a merge, Stewart wants the content checks from the "Daily website smoke test" scheduled
task run against the live site. Certificate checks are not needed on merges.

- **If you are watching the PR and its merge event reaches you:** wait for the "Deploy to GitHub
  Pages" run on the merge commit to finish, then run the checks yourself and report the results.
- **Otherwise** (you only see the merge afterwards, or Stewart mentions merging): remind Stewart
  to have the checks run, and offer to run them right then.

The checks, read-only (report results, never change anything):

1. **Page:** https://www.theocmusical.com loads over HTTPS with the title
   "The O.C. The Musical", the logo, the cast hero image, and the "Watch the show", "About",
   "Critical acclaim" and "Hear a sneak peek" sections. ("Hear a sneak peek" uses an embedded
   player, so it can look empty in fetched HTML; that's fine.)
2. **Images and links:** run the site-check Python script stored in the "Daily website smoke
   test" scheduled task's prompt (read it with the `list_triggers` / `get_trigger` tools), saved
   to the scratchpad exactly as written and run with `python3 -I`. It checks all three of
   Stewart's sites; report this site's results and mention anything broken on the others.
   The 2015 Vancouver Fringe ticket links and old press reviews are "historical" and expected
   to be dead; Facebook/X and 401/403/429 responses are "couldn't verify", not broken.
3. **The change itself:** confirm what the merged PR changed is visible on the live site.
