### do not translate into windows paths e.g ("$(pwd)/../../2024_02_03_delta_format":/opt/spark/work-dir/"$(pwd)/../../2024_02_03_delta_format":/opt/spark/work-dir/)
export MSYS_NO_PATHCONV=1

### set aliat to run docker correctly
alias docker='winpty docker'