FROM debian:buster
WORKDIR /app

RUN apt-get update && \
    apt-get -y upgrade && \
    apt-get -y install wget bzip2 python3 python3-pip texlive texlive-latex-base texlive-luatex texlive-latex-recommended texlive-latex-extra texlive-fonts-extra texlive-lang-all && \
    pip3 install patacrep && \
    # Downgrade these 2 libs to make them work with Patacrep
    pip3 install jinja2==3.0 pyYAML==5.4.1 && \
    wget https://lilypond.org/download/binaries/linux-64/lilypond-2.22.2-1.linux-64.sh && \
    # LilyPond's install script expects the user to hit 'Enter', hence the 'echo'
    echo -ne '\n' | sh lilypond-2.22.2-1.linux-64.sh && \
    rm lilypond-2.22.2-1.linux-64.sh && \
    apt-get -y purge wget bzip2 && \
    apt-get -y autoremove && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

CMD ["songbook", "songbook.yaml"]
