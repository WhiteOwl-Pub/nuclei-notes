![banner](images/nuclei-banner.png)
# Useful Options



## target
| Option  | Description | Example |note|
| ------------- | ------------- | -------------- | ----------------- |
| `-u`  | target URLs to scan  |`nuclei -u https://example.com`|all the templates (except nuclei-ignore list) gets executed from default template installation path.|
| `-l`  |  file containing a list of target URLs to scan  |`nuclei -l hosts.txt`|URLs one per line|

## templates

| Option  | Description | Example |note|
| ------------- | ------------- | -------------- | ----------------- |
| `-t`  | template file or template directory paths to include in the scan  |`nuclei -u https://example.com -t cves/ -t exposures/`|Custom template directory or multiple template directory can be executed as follows.|
| `-w`  |   workflow or workflow directory paths to include in the scan  |`nuclei -u https://example.com -w workflows/`|Workflows allow users to define an execution sequence for templates. The templates will be run on the defined conditions.|
 `-tl`  |   list all available templates  |`nuclei -tl`||


## output

| Option  | Description | Example |note|
| ------------- | ------------- | -------------- | ----------------- |
| `-o`  | output file to write found issues/vulnerabilities  |`nuclei -u https://example.com -o report`||
| `-json`  |   write output in JSONL(ines) format  |`nuclei -u https://example.com --json -o report.json`||

## other

| Option  | Description | Example |note|
| ------------- | ------------- | -------------- | ----------------- |
| `-tags`  | execute a subset of templates that contain the provided tags  |`nuclei -u https://example.com -tags config -t exposures/`|all the templates available exposures/ directory and has config tag in it.|
| `-rl`  |   maximum number of requests to send per second  |`nuclei -u https://example.com -rl 25`|default 150|
|`-v`  |    show verbose output  |`nuclei -v -u https://example.com `||
| `-update`  | update nuclei engine to the latest released version  |`nuclei -update`||
| `-ut`  | update nuclei-templates to latest released version  |`nuclei -ut`||


## examples

```
`nuclei -u https://example.com -t cves/ -t default-logins/ -t exposed-panels/ -t exposures/ -t file/ -rl 43 -v -o nuclei-report` testing several templates

`nuclei -u https://example.com -tags cve -rl 97 -o nuclei-report` testing all templates that have cve tag

`nuclei -u https://Example-wordpress.com -w workflows/wordpress-workflow.yaml` testing bundle of templates with workflow
```


## tips: 
- be sure your templates and engine are up to date
- for getting used to adding tags check TOP-10.md in nuclei-templates directory
- each template path must have -t option
- we can use nuclei for fuzzing too in check fuzzing directory. you can use it for 403-bypass,weak-creadentionals and ... 
- check nuclei.projectdiscovery.io for complete documentaion




