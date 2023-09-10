### Hi there 👋
Hi 👋, I'm Pradip Malik.
------------------
--A passionate frontend and backend developement.

-----------------------
I’m currently learning ---- React.js,java Spring,fluter,node.js,mariadb,AWS etc.

-----------------------
TECHNICAL SKILL

-----------------------
• Programming Languages ---- Proficient in Java, MySQL, Java Framework Spring

-----------------------
• Web Development ----- Skilled in HTML, CSS, JavaScript. Bootstrap5 Framework and React.js

-----------------------
• Other --- Solid grasp of Data Structure and Algorithms, Computer Networks, 
 Database Management System

-----------------------
📫 How to reach me ---- pradipmalik2222@gmail.com
-----------------------
📄 Know about my experiences ------ https://drive.google.com/file/d/1RAQHwkJJEXQ-mGL7vA7yhRRRDVGsapk9/view?usp=sharing
-----------------------
https://www.linkedin.com/in/pradip-malik-mca/
-----------------------
https://www.codechef.com/users/pradipmalik
-----------------------
https://www.hackerearth.com/@pradipmalik2222
---------------------

<!--
**PradipProgramming/PradipProgramming** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->

# GitHub Action for generating a contribution graph with a snake eating your contributions.

name: Generate Snake

# Controls when the action will run. This action runs every 6 hours.

on:
  schedule:
      # every 6 hours
    - cron: "0 */6 * * *"

# This command allows us to run the Action automatically from the Actions tab.
  workflow_dispatch:

# The sequence of runs in this workflow:
jobs:
  # This workflow contains a single job called "build"
  build:
    # The type of runner that the job will run on
    runs-on: ubuntu-latest

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:

    # Checks repo under $GITHUB_WORKSHOP, so your job can access it
      - uses: actions/checkout@v2

    # Generates the snake  
      - uses: Platane/snk@master
        id: snake-gif
        with:
          github_user_name: PradipProgramming
          # these next 2 lines generate the files on a branch called "output". This keeps the main branch from cluttering up.
          gif_out_path: dist/github-contribution-grid-snake.gif
          svg_out_path: dist/github-contribution-grid-snake.svg

     # show the status of the build. Makes it easier for debugging (if there's any issues).
      - run: git status

      # Push the changes
      - name: Push changes
        uses: ad-m/github-push-action@master
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          branch: master
          force: true

      - uses: crazy-max/ghaction-github-pages@v2.1.3
        with:
          # the output branch we mentioned above
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
