# Notify Slack Action

Composite GitHub Action to send a message to a Slack channel.

**Intend for internal usage only.**

## Inputs

| Name                   | Required | Description                                                                                                       |
| ---------------------- | -------- | ----------------------------------------------------------------------------------------------------------------- |
| `keeper-secret-config` | `true`   | The Keeper Secret Manager configuration used to retrieve Slack OAuth token from KSM                               |
| `channel-id`           | `true`   | The Slack channel id where to send the message                                                                    |
| `message`              | `true`   | The message to display in first block of notification                                                             |
| `previous-message-ts`  | `false`  | The timestamp of a previous message posted. It will update the existing message instead of posting a new message. |

## Outputs

| Name                | Description                         |
| ------------------- | ----------------------------------- |
| `message-timestamp` | The timestamp of the message posted |

## Usage

```yaml
jobs:
  notify-slack:
    runs-on: ubuntu-latest
    steps:
      - name: Send message to Slack channel
        uses: bonitasoft/notify-slack-action@TAGNAME
        with:
          keeper-secret-config: ${{ secrets.KSM_CONFIG }}
          channel-id: ${{ vars.SLACK_CHANNEL_ID }}
          message: |
            :x: Build on branch ${{ github.ref }} failed.

            <https://github.com/bonitasoft/notify-slack-action| Link example>
```
