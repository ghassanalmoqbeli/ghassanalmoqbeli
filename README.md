name: Generate Snake

on:
  schedule:
    - cron: "0 0 * * *"  # تحديث يومي
  workflow_dispatch:

jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - uses: Platane/snk@master
        with:
          github_user_name: ghassanalmoqbeli
          svg_out_path: dist/snake.svg
      - name: Commit and Push
        run: |
          git config --global user.name "GitHub Actions"
          git config --global user.email "github-actions@github.com"
          git add dist/snake.svg
          git commit -m "Update snake animation"
          git push
