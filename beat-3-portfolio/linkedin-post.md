I built and improved `pr-precheck`, an AI assistant that checks whether a pull request is ready to submit. After its first evaluation, I changed the rubric and improved its agreement from 17 out of 20 cases to 19 out of 20.

The tool checks a proposed change against its issue, plan, tests, and repository rules. My first run showed that I had made one evidence rule too strict, so three valid cases were rejected. I changed the rule, retested those cases, and then ran the full evaluation again.

One case still exposed a gap: the tool missed a repository rule requiring AI-use disclosure. My next step is to make that check more specific and run the evaluation again. This taught me to improve automation by studying its misses, not just its score.

https://github.com/Aayush7788/ai301-coursework/blob/main/beat-3-portfolio/technical-writeup.md
