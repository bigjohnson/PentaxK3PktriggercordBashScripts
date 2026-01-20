#!/bin/bash
DIRECTORY=$(date '+%Y%m%d_%H%M%S')
mkdir "${DIRECTORY}"
if [ ! -d "${DIRECTORY}" ]
then
	echo Cannot create directory ${DIRECTORY}
	exit 1
fi

if [ -f image-0000.dng ]
then
	rm image-0000.dng 
fi
#if [ -f image.dng ]
#then
#	rm image.dng 
#fi
echo 0
pktriggercord-cli --model=K-7 --file_format=DNG -m=GREEN --exposure_compensation=0 -o image.dng --timeout=10
mv image-0000.dng ${DIRECTORY}/image.dng
sleep .2
for EXPOSURE in +1 -1 +2 -2 +3 -3
do
	echo ${EXPOSURE}
	if [ -f image${EXPOSURE}.dng ]
	then
		rm image${EXPOSURE}.dng 
	fi
	pktriggercord-cli --model=K-7 --file_format=DNG -m=GREEN --exposure_compensation=${EXPOSURE} -o image.dng --timeout=10
	mv image-0000.dng ${DIRECTORY}/image${EXPOSURE}.dng
	sleep .2
done
