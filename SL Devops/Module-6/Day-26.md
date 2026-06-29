# Task - 1
```
sudo apt install gh -y
```
<img width="1103" height="840" alt="image" src="https://github.com/user-attachments/assets/7c112acc-fb96-4e01-bcf6-86a90f310a22" />

- Web application authentication
- Personal Access Token
- SSH Authentication
- Env variable authentication

# Task - 2
```
gh repo create gh-cli-test \
  --public \
  --clone \
  --add-readme

git repo clone <username>/<reponame>
gh repo view , gh repo view <username>/<repo-name> --web<>
gh repo list -10 gh repo list <your-github-username>
gh repo view --web // gh repo view <username>/<repo-name> --web
gh repo delete gh-cli-test
```

# Task - 3
```
gh issue create \
  --title "Fix login page bug" \
  --body "The login button is not responding when clicked. Investigate and fix the issue." \
  --label "bug"
gh issue list
gh issue view 1
gh issue close 1
```
<img width="1917" height="571" alt="image" src="https://github.com/user-attachments/assets/548ef9ed-83e5-417d-ae8c-cddea89a0f4a" />
<img width="1201" height="608" alt="image" src="https://github.com/user-attachments/assets/f91e8813-9b9c-4930-8547-064544c13734" />

# Task - 4

```
git switch -c task-4
nano Readme.md
git status(red)
git add readme.md/git commit-m/git push -u(upstream) origin Task-4
```
<img width="1211" height="993" alt="image" src="https://github.com/user-attachments/assets/c1e1aaf1-2ee0-4c0e-a598-d02d174930ce" />
<img width="1456" height="570" alt="image" src="https://github.com/user-attachments/assets/266e9802-e75c-43af-90b3-291c95729570" />
<img width="901" height="425" alt="image" src="https://github.com/user-attachments/assets/033bffdb-aef2-4ce1-b46b-833deb2d1760" />

# Task - 5
### How could `gh run` and `gh workflow` be useful in a CI/CD pipeline?

### `gh workflow`

- Lists all workflows in a repository.
- Enables, disables, or triggers workflows.
- Helps manage GitHub Actions directly from the terminal.
- Eliminates the need to use the GitHub web interface.

### `gh run`
- Lists workflow execution history.
- Displays the status of builds and deployments.
- Views logs for troubleshooting failed pipelines.
- Watches workflows in real time.
- Can rerun failed workflows from the command line.

## Benefits in CI/CD
- Monitor builds without opening GitHub.
- Debug failures quickly by viewing logs.
- Trigger workflows from scripts.
- Integrate GitHub Actions management into automation.
- Improve developer productivity by keeping everything in the terminal.

# Task - 6
<img width="1263" height="980" alt="image" src="https://github.com/user-attachments/assets/339b122f-f751-41a8-a340-67e87f1c366f" />
<img width="1263" height="980" alt="image" src="https://github.com/user-attachments/assets/e7c23579-72ac-461c-b45c-563a70cf35c0" />
<img width="1777" height="980" alt="image" src="https://github.com/user-attachments/assets/ed853528-42dd-478c-8a21-27f15ad71f99" />
