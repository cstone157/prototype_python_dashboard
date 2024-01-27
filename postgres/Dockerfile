FROM postgres:12.10

# Delete our left over sample_data.sql
RUN mkdir preloaded_data

# COPY ALL OF OUR DATA_SHEETS OVER (We copy all of them over since there's no conditional COPY)
COPY ./pg_sample_data/adsb/*.sql \
		./pg_sample_data/random/*.sql \
		/preloaded_data/

# Retrieve all of the files from the folder
RUN file="$(ls -1 /preloaded_data)" && echo $file

RUN array=$(ls ./preloaded_data -1); for i in ${array}; do cp ./preloaded_data/$i /docker-entrypoint-initdb.d/$i; echo $i; done

# Cleanup
RUN rm -rf /preloaded_data