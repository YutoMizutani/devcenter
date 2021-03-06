---
title: Step outputs
tag:
- steps
- " workflows"
- env vars
- bitrise.yml
summary: Step outputs are environment items that are the result of running a given
  step. For example, the deploy-to-bitrise-io step generates the $BITRISE_PUBLIC_INSTALL_PAGE_URL
  and the $BITRISE_PUBLIC_INSTALL_PAGE_URL_MAP output variables by default.
redirect_from: []
menu:
  bitrise-cli-main:
    weight: 23

---
Step outputs are environment items that are the result of running a given step. For example, the `deploy-to-bitrise-io` step generates the `$BITRISE_PUBLIC_INSTALL_PAGE_URL` and the `$BITRISE_PUBLIC_INSTALL_PAGE_URL_MAP` output variables by default. You can check out the default outputs of a step in the `Workflow Editor` on [bitrise.io](https://www.bitrise.io) or in the `step.yml` file of the step.

Step outputs can be defined in the `step.yml` file of the project by setting the `outputs` attribute. They have the same syntax as every environment property. It consists of two main parts: a `KEY: value` pair and an `opts` field. The key and the value are required, the `opts` field is optional.

``` yaml
- MY_KEY_FOR_THE_ENV: my value for the env
  opts:
    title: An example env var item
    is_dont_change_value: false
    category: example
```

`MY_KEY_FOR_THE_ENV`: the key of the environment item (required)
`my value for the env`: the value of the item (required)
`opts`: optional attributes.

## Exporting step outputs in output aliases

The default outputs of a step cannot be changed by the user in the `bitrise.yml` file of the project, it can only be changed in the `step.yml` file. However, you can export the output in a custom environment variable. This is useful, for example, if you have the same step twice in your workflow and you wish to use the generated output of both steps.

1. Open the `bitrise.yml` file of your project.

   You can do this either on [bitrise.io](https://www.bitrise.io) or locally.
2. Find the step you need.
3. Set the `outputs` attribute: specify the original environment key - the default output that the step generates - and the alias.

**Example**:

``` yaml
workflows:
  primary:
  steps:
  - gradle-runner:
      outputs:
      - BITRISE_APK_PATH: ALIAS_APK_PATH
```

In the example, the value for the `BITRISE_APK_PATH` environment variable will be exported under the `ALIAS_APK_PATH` key.

<div class="banner">
	<img src="/assets/images/banner-bg-888x170.png" style="border: none;">
	<div class="deploy-text">Check out your build's Steps</div>
	<a target="_blank" href="https://app.bitrise.io/dashboard/builds"><button class="button">Go to your app</button></a>
</div>