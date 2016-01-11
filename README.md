hadoop jar /usr/hdp/2.3.2.0-2950/hadoop-mapreduce/hadoop-streaming.jar \
 -D mapred.reduce.tasks=2 \
 -input /user/mythijraman4833/sample.txt  \
 -output /user/mythijraman4833/out.txt  \
 -inputformat org.apache.hadoop.mapred.KeyValueTextInputFormat  \
 -outputformat org.apache.hadoop.mapred.SequenceFileOutputFormat \
 -mapper " sed "s/\(.\)/\1\n/g" | sed "s/[^A-Za-z]//g" | tr "A-Z" "a-z" | sort "  \
 -reducer "uniq -c"
 
