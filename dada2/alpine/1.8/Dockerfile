# DADA2
#
# VERSION               1.8.0__bcw.0.3.0

FROM      alpine:3.8
# For singularity on the hutch cluster
RUN mkdir /fh && mkdir /app && mkdir /src
RUN mkdir -p /mnt/inputs/file && mkdir -p /mnt/outputs/file && mkdir /scratch && mkdir /working
RUN apk add --no-cache bash \
python3==3.6.4-r1 \
R==3.5.0-r1 \
R-dev==3.5.0-r1 \
build-base
RUN pip3 install \
awscli>=1.15.14 \
boto3>=1.7.14 \
bucket_command_wrapper==0.3.0 

# Manually install dependencies :<
# 'Rcpp' ‘Biostrings’, ‘ggplot2’, ‘data.table’, ‘reshape2’, ‘ShortRead’, ‘RcppParallel’
RUN     Rscript -e "install.packages('Rcpp', repos='https://cran.mtu.edu/')"
RUN     Rscript -e "install.packages('ggplot2', repos='https://cran.mtu.edu/')"
RUN     Rscript -e "source('https://bioconductor.org/biocLite.R'); biocLite('Biostrings')"
RUN     Rscript -e "install.packages('data.table', repos='https://cran.mtu.edu/')"
RUN     Rscript -e "install.packages('reshape2', repos='https://cran.mtu.edu/')"
RUN     Rscript -e "source('https://bioconductor.org/biocLite.R'); biocLite('ShortRead')"
RUN     Rscript -e "install.packages('RcppParallel', repos='https://cran.mtu.edu/')"

# Download dada2 tgz directly so we can hope to version 
RUN wget https://bioconductor.org/packages/3.7/bioc/src/contrib/dada2_1.8.0.tar.gz
RUN R CMD INSTALL dada2_1.8.0.tar.gz

