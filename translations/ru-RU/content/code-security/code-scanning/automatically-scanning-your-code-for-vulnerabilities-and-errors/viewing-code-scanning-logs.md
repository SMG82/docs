---
title: Viewing code scanning logs
intro: 'You can view the output generated during {% data variables.product.prodname_code_scanning %} analysis in {% data variables.product.product_location %}.'
product: '{% data reusables.gated-features.code-scanning %}'
permissions: 'If you have write permissions to a repository, you can view the {% data variables.product.prodname_code_scanning %} logs for that repository.'
miniTocMaxHeadingLevel: 4
redirect_from:
  - /code-security/secure-coding/automatically-scanning-your-code-for-vulnerabilities-and-errors/viewing-code-scanning-logs
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
topics:
  - Security
shortTitle: View code scanning logs
---

{% data reusables.code-scanning.beta %}
{% data reusables.code-scanning.enterprise-enable-code-scanning-actions %}

## About your {% data variables.product.prodname_code_scanning %} setup

You can use a variety of tools to set up {% data variables.product.prodname_code_scanning %} in your repository. For more information, see  "[Setting up {% data variables.product.prodname_code_scanning %} for a repository](/code-security/secure-coding/automatically-scanning-your-code-for-vulnerabilities-and-errors/setting-up-code-scanning-for-a-repository#options-for-setting-up-code-scanning)."

{% ifversion fpt or ghes > 3.1 or ghae-next or ghec %}
The log and diagnostic information available to you depends on the method you use for {% data variables.product.prodname_code_scanning %} in your repository. You can check the type of {% data variables.product.prodname_code_scanning %} you're using in the **Security** tab of your repository, by using the **Tool** drop-down menu in the alert list. For more information, see "[Managing {% data variables.product.prodname_code_scanning %} alerts for your repository](/code-security/secure-coding/automatically-scanning-your-code-for-vulnerabilities-and-errors/managing-code-scanning-alerts-for-your-repository#viewing-the-alerts-for-a-repository)."

## About analysis and diagnostic information

You can see analysis and diagnostic information for {% data variables.product.prodname_code_scanning %} run using {% data variables.product.prodname_codeql %} analysis on {% data variables.product.prodname_dotcom %}.

**Analysis** information is shown for the most recent analysis in a header at the top of the list of alerts. For more information, see "[Managing code scanning alerts for your repository](/code-security/secure-coding/automatically-scanning-your-code-for-vulnerabilities-and-errors/managing-code-scanning-alerts-for-your-repository#viewing-the-alerts-for-a-repository)."

**Diagnostic** information is displayed in the Action workflow logs and consists of summary metrics and extractor diagnostics. For information about accessing {% data variables.product.prodname_code_scanning %} logs on {% data variables.product.prodname_dotcom %}, see "[Viewing the logging output from {% data variables.product.prodname_code_scanning %}](#viewing-the-logging-output-from-code-scanning)" below.

If you're using the {% data variables.product.prodname_codeql_cli %} outside {% data variables.product.prodname_dotcom %}, you'll see diagnostic information in the output generated during database analysis. This information is also included in the SARIF results file you upload to {% data variables.product.prodname_dotcom %} with the {% data variables.product.prodname_code_scanning %} results.

For information about the {% data variables.product.prodname_codeql_cli %}, see "[Configuring {% data variables.product.prodname_codeql_cli %} in your CI system](/code-security/secure-coding/using-codeql-code-scanning-with-your-existing-ci-system/configuring-codeql-cli-in-your-ci-system#viewing-log-and-diagnostic-information)."

### About summary metrics

{% data reusables.code-scanning.summary-metrics %}

### About {% data variables.product.prodname_codeql %} source code extraction diagnostics

{% data reusables.code-scanning.extractor-diagnostics %}

{% endif %}
## Дальнейшие шаги

This section applies to {% data variables.product.prodname_code_scanning %} run using {% data variables.product.prodname_actions %} ({% data variables.product.prodname_codeql %} or third-party).

After setting up {% data variables.product.prodname_code_scanning %} for your repository, you can watch the output of the actions as they run.

{% data reusables.repositories.actions-tab %}

  You'll see a list that includes an entry for running the {% data variables.product.prodname_code_scanning %} workflow. The text of the entry is the title you gave your commit message.

  ![Actions list showing {% data variables.product.prodname_code_scanning %} workflow](/assets/images/help/repository/code-scanning-actions-list.png)

1. Click the entry for the {% data variables.product.prodname_code_scanning %} workflow.

2. Click the job name on the left. For example, **Analyze (LANGUAGE)**.

  ![Log output from the {% data variables.product.prodname_code_scanning %} workflow](/assets/images/help/repository/code-scanning-logging-analyze-action.png)

1. Review the logging output from the actions in this workflow as they run.

1. After a scan completes, you can view alerts from a completed scan. For more information, see "[Managing {% data variables.product.prodname_code_scanning %} alerts for your repository](/code-security/secure-coding/managing-code-scanning-alerts-for-your-repository#viewing-the-alerts-for-a-repository)."

{% note %}

After you commit the workflow file or create a pull request, {% data variables.product.prodname_code_scanning %} will analyze your code according to the frequency you specified in your workflow file. If you created a pull request, {% data variables.product.prodname_code_scanning %} will only analyze the code on the pull request's topic branch until you merge the pull request into the default branch of the repository.

{% ifversion fpt or ghes > 3.1 or ghae or ghec %}
  ![Click the "n alerts found" link](/assets/images/help/repository/code-scanning-alerts-found-link.png)
{% else %}
  ![Click the "n alerts found" link](/assets/images/enterprise/3.1/help/repository/code-scanning-alerts-found-link.png)
{% endif %}

{% endnote %}
