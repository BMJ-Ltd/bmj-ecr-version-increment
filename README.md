
# BMJ

This GHA will check a given repository and increment a version number

The version number must be in the format of major.minor.patch like 1.2.3

If no such version is found on any of the images that are already in the ECR a new version number 0.0.1 
will be created by default.




## Environment Variables

To run this project, you will need to have all the correct GitHub secrets set to access the ECR in AWS


## Usage/Examples

The two required parameters are the ***ecr_name*** and the ***patch***

Valid parameters for patch are 
* major
* minor
* patch

Where ***major*** will increase the ***major*** version and set the ***minor*** and ***patch*** to zero

Where ***minor*** will increase the ***minor*** version and set the ***patch*** to zero

Where ***patch*** will increase the ***patch*** version

### Add this to your gitHubWorkflow


```

name: Tester-Run
on: [push, pull_request]
jobs:
  build:
    name: Get Last Version Number
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v1

      - name: BMJ Github Action to retrieve the latest version number from ECR
        uses: BMJ-Ltd/bmj-ecr-version-increment@1.0.0
        id: version
        with:
          ecr_name: "xxx-xxx-xxx"
          version_type: "patch"
      - name: Get the version
        run: |
          echo '${{ steps.version.outputs.newVersion }}'



```


# Hi, I'm Mike! 👋


## 🚀 About Me
I'm a DevOps Engineer in BMJ
