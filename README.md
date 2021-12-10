# Code Sign Composite Action

### Parameters
| Name | Type |      | Default | Note | 
| ---- | ---- | ---- | ----- | ---- |
`group_id` | Integer | Required* | `11` | Defaults to `gg-app-ncipher-csg-p-da-team` id
`signing_profile_id` | Integer | Required* | `4` | Defaults to `jar` signing profile id
`artifact_path` | String | Required* | `${{ github.workspace }}` 
`artifact_name` | String | Required* |
`csg_username` | String | Required* | `sa-digitalit-dss`
`csg_password` | Secret | Required* |
`ghes_pat` | Secret | Required* | | Required for downloading CSG CLI from GitHub Release
`csg_output_filename` | String | *Optional*

Usage:
```yaml
   - uses: sherwin-williams-co/sw-code-sign-composite-action@main
      with:
        group_id: 11
        signing_profile_id: 4
        artifact_path: ${{ github.workspace }}
        artifact_name: 'HelloWorld.jar'
        csg_username: 'sa-digitalit-dss'
        csg_password: ${{ secrets.CSG_PASSWORD }}
        ghes_pat: {{ secrets.GITHUB_TOKEN }} # this will be 'ghec_pat' once repo moves
        csg_output_filename: 'Signed_<filename>'
```
