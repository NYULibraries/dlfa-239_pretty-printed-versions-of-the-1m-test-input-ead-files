# Pretty-printed versions of the 1M+ test input EAD files

Jira: [DLFA-239: Create GitHub repo with pretty\-printed versions of the 1M\+ test input EAD files](https://jira.nyu.edu/browse/DLFA-239)

# How this repo was created

Environment vars:

`SOURCE_DIR` = root of local clone of [findingaids\_eads\_v2](https://github.com/NYULibraries/findingaids_eads_v2/) set to [8d1b8fb6bd45327e90857c77bff8afa66358f4e7](https://github.com/NYULibraries/findingaids_eads_v2/tree/8d1b8fb6bd45327e90857c77bff8afa66358f4e7) (per [DLFA-201: Specify acceptance test suite for v2 indexer](https://jira.nyu.edu/browse/DLFA-201))

`TARGET_DIR` = root of local clone of this repo

```shell
for f in $( find $SOURCE_DIR -type f -name *.xml )
do 
    repository=$( basename $( dirname $f ) )
    filename=$( basename $f )
    targetDirectory="$TARGET_DIR/$repository"
    mkdir -p $targetDirectory
    targetFile=$targetDirectory/$filename
    cat $f | xmllint --format - > $targetFile
done
```