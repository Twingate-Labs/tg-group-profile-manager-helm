# tg-group-profile-manager-helm
Manage your Twingate group profile through Slack.

## Installing the Chart

To install the chart
```shell
$ helm repo add twingate-labs https://twingate-labs.github.io/tg-group-profile-manager-helm/
$ helm install tg-group-profile-manager twingate-labs/tg-group-profile-manager -n [namespace] \
    --set variables.twingateAccount="xxx.twingate.com" \
    --set variables.twingateApiKey="xxx" \
    --set variables.slackSigningSecret="xxx" \
    --set variables.slackBotToken="xoxb-xxx" \
    --set-json='variables.profileConfig={"profiles":[{"profileName":"Example One Of Profile 1","profileType":"oneOf","groups":["Prod","Preprod","Testing"],"applicableToGroup":"Everyone"},{"profileName":"Example One Of Profile 2","profileType":"oneOf","groups":["US","EU","ASIA"],"applicableToGroup":"Everyone"},{"profileName":"Example Self-Serve Business Approvals","profileType":"selfServeApproval","groups":["HR","Finance","Sales"],"timeOptions": ["Forever", "1h", "8h", "24h", "7d", "30d", "90d"],"applicableToGroup":"Everyone","approverGroup":"IT"}, {"profileName":"Example Self-Serve Business Approvals 2","profileType":"selfServeApproval","groups":["HR","Finance","Sales"],"timeOptions": ["Forever", "1h", "8h", "24h"],"applicableToGroup":"Everyone","approverGroup":"IT"}],"groupPermissions":{"Prod":"Admin"}}'
```

- `SLACK_SECRET` Slack signing secret
- `SLACK_BOT_TOKEN` Slack bot token (begins with `xoxb-`)
- `TG_API_KEY` can be generated in the Setting page within the Twingate Admin Console (Read and Write permission is required)
- `TG_ACCOUNT` replace with your Twingate Network Address (e.g. _test1.twingate.com_)
- `PROFILE_CONFIG` Your profile configuration (see notes and guidance in the [schema documentation](./docs/SCHEMA.md))

For setting up with secret, see [setup with secret](./docs/WITH_SECRET.md)

For setting up with https/ingress, see [setup with ingress](./docs/WITH_INGRESS.md)

For setting up with resource requests and limits, see the `resources` section in [value.yaml](./values.yaml)