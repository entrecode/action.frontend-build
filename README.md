# action.frontend-build

GitHub composite action for frontend-build

## example

```yaml
deploy:
    runs-on: ubuntu-latest
    
    permissions:
      contents: read

    needs: build

    steps:
    - name: frontend build and upload action
      id: build-frontend-action
      uses: entrecode/action.frontend-build@latest
      with:
        PAT: ${{ secrets.PAT }}
        NODE_VERSION: ${{ vars.NODE_VERSION }}      # optional - default is 'latest'
        WORKING_DIRECTORY: ${{ vars.WORKING_DIRECTORY }}
        BUCKET_NAME: ${{ vars.BUCKET_NAME }}
        OUTPUT_PATH: ${{ vars.OUTPUT_PATH }}        # optional - default is 'dist'
```

## inputs

All inputs are requried to run the action

| Name                | Type     | Description                                                                                                                |
|---------------------|----------|----------------------------------------------------------------------------------------------------------------------------|
| `PAT`               | String   | Personal Access Token as GitHub secret                                                                                     |
| `NODE_VERSION`      | String   | NODE_VERSION for Project - default is `latest`. Examples: 16.x, 10.15.1, >=10.15.0, lts/Hydrogen, 16-nightly, latest, node |
| `WORKING_DIRECTORY` | String   | WORKING_DIRECTORY of the project. Examples: `apps/app_name/admin`, `admin`                                                 |
| `BUCKET_NAME`       | String   | Default-Name of the s3 bucket without `-stage` or `-prod`                                                                  |
| `OUTPUT_PATH`       | String   | OUTPUT_PATH of the build - default is `dist`                                                                               |

`PAT` is defined in GitHub as action-secrets. `NODE_VERSION`, `WORKING_DIRECTORY`, `BUCKET_NAME` and `OUTPUT_PATH` are defined in GitHub as action-variables. `NODE_VERSION` and `OUTPUT_PATH` are not required.
