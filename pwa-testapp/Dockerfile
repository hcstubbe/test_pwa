FROM rocker/r-ver:4.1.2
RUN apt-get update && apt-get install -y  git-core libcurl4-openssl-dev libgit2-dev libicu-dev libmariadb-dev libssl-dev libxml2-dev make pandoc pandoc-citeproc && rm -rf /var/lib/apt/lists/*
RUN echo "options(repos = c(CRAN = 'https://cran.rstudio.com/'), download.file.method = 'libcurl', Ncpus = 4)" >> /usr/local/lib/R/etc/Rprofile.site
RUN R -e 'install.packages("remotes")'
RUN Rscript -e 'remotes::install_version("shiny",upgrade="never")'
RUN Rscript -e 'remotes::install_version("shinyMobile",upgrade="never")'

COPY ./app /app

EXPOSE 3838

WORKDIR /app

CMD ["R", "-e", "shiny::runApp(host = '0.0.0.0', port = 3838)"]