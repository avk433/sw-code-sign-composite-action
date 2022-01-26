# Code Sign Composite Action

### Parameters
| Name | Type |      | Default | Note | 
| ---- | ---- | ---- | ------- | ---- |
`group_id` | Integer | Required* | 
`signing_profile_id` | Integer | Required* |
`artifact_path` | String | Required* | `${{github.workspace}}` 
`artifact_name` | String | Required* |
`csg_username` | String | Required* |
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
        csg_username: ${{ secrets.CSG_USERNAME }}
        csg_password: ${{ secrets.CSG_PASSWORD }}
        ghes_pat: ${{ secrets.GITHUB_TOKEN }} # this will be 'ghec_pat' once repo moves
        # Optional
        # csg_output_filename: 'Signed_<filename>'
```
