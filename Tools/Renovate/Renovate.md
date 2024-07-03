# Renovate

Renovate is a dependency updater, it integrates into your repositories and allows for automation of dependencies updates via merge requests.

[Official documentation](https://docs.renovatebot.com)

## Basic concepts

### Major elements

#### extends

Exemple:

```json
{
	"extends": [
	        // Best-practices Presets
	        "config:recommended",
	        "docker:pinDigests",
	        "helpers:pinGitHubActionDigests",
	        ":pinDevDependencies"
	        // Default Presets
	        ':dependencyDashboard',
	        ':semanticPrefixFixDepsChoreOthers',
	        ':ignoreModulesAndTests',
	        // Groupe Presets
	        'group:monorepos',
	        'group:recommended',
	        // Replacement Presets
	        'replacements:all',
	        // Security Presets
	        'security:openssf-scorecard',
	        // Workaround Presets
	        'workarounds:all',
	]
}
```

A list of presets can be found [here](https://docs.renovatebot.com/config-presets/).

More about presets [here](https://docs.renovatebot.com/key-concepts/presets/).
#### customManagers

Exemple with docker images in Gitlab-ci files:

```json
{
	"customManagers": [
	        {
	            "customType": "regex",
	            "datasourceTemplate": "docker",
	            "description": "Update docker references in gitlab variables",
	            "fileMatch": [
	                "\\.gitlab-ci\\.ya?ml$",
	                "\\templates/*.ya?ml$"
	            ],
	            "matchStrings": [
	                "CI_RENOVATE_IMAGE[A-Z_]*\\s*:\\s*(?<depName>[^:]+?):(?<currentValue>[a-z0-9.-]+)(?:@(?<currentDigest>sha256:[a-f0-9]+))?"
	            ],
	            "versioningTemplate": "docker"
	        }
	]
}
```

Exemple with maven in pom.xml files:

```json
{
	"customManagers": [
	        {
	            "customType": "regex",
	            "datasourceTemplate": "{{#if datasource}}{{{datasource}}}{{else}}maven{{/if}}",
	            "fileMatch": [
	                "(^|/)pom\\.xml$"
	            ],
	            "matchStrings": [
	                "<!--\\s?renovate:( datasource=(?<datasource>[a-z-.]+?))? depName=(?<depName>[^\\s]+?)(?: packageName=(?<packageName>[^\\s]+?))?(?: versioning=(?<versioning>[^\\s]+?))?(?: extractVersion=(?<extractVersion>[^\\s]+?))?\\s+-->\\s+<.+\\.version>(?<currentValue>.+)<\\/.+\\.version>"
	            ],
	            "versioningTemplate": "{{#if versioning}}{{{versioning}}}{{/if}}"
	        }
	]
}
```
#### packageRules

Exemple:

```json
{
	"packageRules": [
	        {
	            "automergeType": "pr",
	            "commitBody": "BREAKING CHANGE",
	            "description": "Trigger breaking release for major updates",
	            "matchPackageNames": [
	                "renovate/renovate"
	            ],
	            "matchUpdateTypes": [
	                "major"
	            ],
	            "semanticCommitType": "feat"
	        }
	]
}
```

### Access to repositories

Dependent on your Git provider, most likely handled by an access token.
### Merge requests
### Dependency Dashboard
### Configuration

#### config.js

#### default.json
