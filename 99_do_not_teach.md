# Creating a GitHub repo from your computer

GitHub provides an API that lets you create a GitHub repository from your machine. From the shell you can use something like:

    curl -u 'YOUR_GITHUB_USERNAME' https://api.github.com/user/repos -d '{"name":"YOUR_REPO_NAME","description":"REPO_DESCRIPTION"}'

