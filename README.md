# Code Sign Composite Action

### Profiles

| ID | Name | Uses | Public/Internal        | Hash   |
| --- | --- |---|------------------------|--------|
| 1 | 	OV - Public Trust - Jarsigner | Can be used for signing Jar and war files | Public Trust (OV Level) | SHA1   | 
| 2 | OV - Public Trust - Signtool | Can be used to sign executables | Public (OV Level)      | SHA1   |
| 3 | EV - Public Trust - Signtool | Can be used to sign executables | Public (EV Level - Highest possible) | SHA1   | 
| 4 | 	Int- JarSigning | Can be used to sign jars and wars | Internally trusted | SHA1   |
| 5 | Int - SignTool | Can be used for signing executables | Internally trusted | SHA1   | 
| 6 | Int - SignTool - SHA 256 | Can be used for signing executables | Internally trusted | SHA256 | 

**NOTE: _Groups are explicitly granted access to a subset of these profiles. Groups are only granted access to the 
publicly trusted profiles at the discretion of the PKI team. To see what profiles your group has access to, use the 
profiles command in the csg cli ([Repo with usage guide here](https://github.com/sherwin-williams-co/csg-cli))._**

### How to get access

To get access to the CSG application, either submit a ticket to **SDP - PAM/PKI** or send an email to [pki.admins@sherwin.com](mailto:pki.admins@sherwin.com)

#### What is my group ID?
To find out your group id, you will need to use the csg cli. The GH action will run the profiles command to provide 
additional information. 

### Parameters
| Name | Type |      | Default | Note | 
| ---- | ---- | ---- | ------- | ---- |
`group_id` | Integer | Required* | 
`signing_profile_id` | Integer | Required* |
`artifact_path` | String | Required* | `${{github.workspace}}` 
`artifact_name` | String | Required* |
`csg_username` | String | Required* |
`csg_password` | Secret | Required* |
`jf_artifactory_token` | Secret | Required* | | Use: `${{ secrets.JF_ARTIFACTORY_TOKEN }}`
`csg_output_filename` | String | *Optional* | `Signed_<input_filename>`

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
        jf_artifactory_token: ${{ secrets.JF_ARTIFACTORY_TOKEN }}
        # Optional
        # csg_output_filename: 'Signed_<filename>'
```
