### Install perf
>> sudo apt-get install perf

WARNING: perf not found for kernel 3.16.0-50
You may need to install the following packages for this specific kernel:
    linux-tools-3.16.0-50-generic
    linux-cloud-tools-3.16.0-50-generic
    
>> sudo apt-get install linux-tools-3.16.0-50-generic linux-cloud-tools-3.16.0-50-generic

### use perf to analysis
>> sudo perf record -F 99 -p $pid -g -- sleep 30
>> sudo perf report -n --stdio

### flame graph tool
>> git clone https://github.com/brendangregg/FlameGraph.git
