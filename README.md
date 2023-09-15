# Update-Environment-Variable

This is a GitHub Action to update environment variable in a workflow run.
If the variable does not exist in the environment, it will be created.

## Usage
### Usage with single environment
```YAML 
- name: Update Environment Variable
  uses: MandalAutomations/Update-Environment-Variable@v1
  with:
    Name: "Name of the variable"
    Value: "Value of the variable"
    EnvironmentName: "Environment name"
    RepoId: ${{ github.repository_id }}
    Token: ${{ secrets.PAT_TOKEN }}
```

### Usage with multiple environments
```YAML
update_environment_variable:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        enviornments: ["main", "test", "uat"]

    steps:
      
      - name: Update Environment Variable
        uses: MandalAutomations/Update-Environment-Variable@v6
        with:
            Name: "Name of the variable"
            Value: "Value of the variable"
            EnvironmentName: ${{ matrix.enviornments }}
            RepoId: ${{ github.repository_id }}
            Token: ${{ secrets.PAT_TOKEN }}
```

## Inputs
### Name: 
`Required` `String` Name for the variable to update

### Value:
`Required` `String` Value for the variable to update

### EnvironmentName: 
`Required` `String` Environment Name

### RepoId: 
`Required` `String` Repository ID can be found using  ${{ github.repository_id }}

### Token: 
`Required` `String` Personal Access Token (PAT)