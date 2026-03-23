#TEST

```bash
## folders and filepaths
INPUT_FOLDER=../raw_reads
OUTPUT_FOLDER=../trimmed_reads
IN_R1_LIST=($(tail -n +2 ../Total_RNA_metadata.txt | awk '{print $2}'))
IN_R2_LIST=($(tail -n +2 ../Total_RNA_metadata.txt | awk '{print $3}'))
echo ${IN_R1_LIST[@]}
echo ${IN_R2_LIST[@]}

## Test run trim paired end reads commands
echo "trim_galore commands to trim paired end reads"
parallel --link --dry-run \ 
"trim_galore -j 4 -o $OUTPUT_FOLDER \
--paired $INPUT_FOLDER/{1} $INPUT_FOLDER/{2}" \
::: ${IN_R1_LIST[@]} ::: ${IN_R2_LIST[@]}

## trim paired end reads commands
parallel --link \
"trim_galore -j 4 -o $OUTPUT_FOLDER \
--paired $INPUT_FOLDER/{1} $INPUT_FOLDER/{2}" \
::: ${IN_R1_LIST[@]} ::: ${IN_R2_LIST[@]}
```
