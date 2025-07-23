# Using Safety as a GitHub Action

Safety can be integrated into your existing GitHub CI pipeline as an action. Just add the following as a step in your workflow YAML file after setting your `SAFETY_API_KEY` secret on GitHub under Settings -> Secrets -> Actions:

```yaml
      - uses: pyupio/safety-action@v1
        with:
          api-key: ${{ secrets.SAFETY_API_KEY }}
```

(Don't have an API Key? You can sign up for one with [https://safetycli.com/resources/plans](https://safetycli.com/resources/plans).)

This will run Safety scan and it'll fail your CI pipeline if vulnerable packages are found depending on your policy settings.

Without modifications to the above workflow, the policy settings are automatically loaded from the organization linked to with the `SAFETY_API_KEY`. By default, only vulnerabilities with severity levels `critical`, `high` or `medium` will fail the CI pipeline. You can easily modify the policy via the [Dashboard](https://platform.safetycli.com/organization/policies).

If you have something more complicated such as a monorepo; or once you're finished testing, read the [Documentation](https://docs.safetycli.com/) for more details on configuring Safety as an action.
