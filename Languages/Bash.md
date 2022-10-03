### For loop
[Examples](https://www.cyberciti.biz/faq/bash-for-loop/#Loop_with_strings)

```
for ((a=1; a <= 5 ; a++))
do
   echo "Welcome $a times."
done

******************************

for VARIABLE in {1 .. N}
do
	command1 on $VARIABLE
	command2
	commandN
done

******************************

for OUTPUT in $(Linux command)
do
	command1 on $output
	command2 on $output
done

******************************

```

Range can also be specified by `seq <start> <step> <end>` e.g `seq 5 -1 1` goes 5 to 1 in steps of -1

