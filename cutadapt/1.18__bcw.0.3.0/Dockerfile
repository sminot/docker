# golob/cutadapt
#
# VERSION               1.18__bcw.0.3.0_al38

FROM      alpine:3.8
# Create some mount points in the container for use by bucket-command-wrapper
RUN mkdir -p /mnt/inputs/file && mkdir -p /mnt/outputs/file && mkdir /scratch && mkdir /working
# Install at least python3 (used by BCW). It's OK to change the specific version of python3 used. 
RUN apk add --no-cache \
bash \
build-base \
make \
gcc \
python3-dev>=3.6.3-r9

# Since we are ONLY installing python3 link to it to make it the default python
RUN ln -s /usr/bin/python3 /usr/bin/python
# Install bucket_command_wrapper via pip, along with boto3 / awscli if we want to use AWS at all
RUN pip3 install \
awscli>=1.15.14 \
boto3>=1.7.14 \
bucket_command_wrapper==0.3.0

# Install cutadapt
RUN pip3 install cutadapt==1.18
