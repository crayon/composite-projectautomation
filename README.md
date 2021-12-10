# Project automation 

GitHub action for adding new issues and pull requests to projects. Note that these input names might change before a stable version is released, so make sure to use version tags so that your workflows don't stop all the sudden.

In your workflow YAML file, you can define a step using this action like this:

```yaml
- name: Project automation
    if: github.event_name == 'issues' || github.event_name == 'pull_request'
    uses: crayon/project-github-action@v1.0.0-beta1
    with:
      project_number: 7
      task_id: ${{ github.event.pull_request.node_id || github.event.issue.node_id }}
      repo-token: ${{ secrets.GITHUB_TOKEN }}
```

This runs if the workflow trigger is either an issue or a pull request, and depending on the event type it will submit the correct `node_id`. 
