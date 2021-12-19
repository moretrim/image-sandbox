FROM jjmerelo/alpine-raku:latest

ARG DIR="/test"
USER root

# Set up directories
RUN mkdir $DIR && chown raku $DIR
COPY --chown=raku test.sh /home/raku
VOLUME $DIR
WORKDIR $DIR

# Extra dependencies
RUN ["apk", "add", "--no-cache", \
    , "bash" \
    , "curl" \
    ]

# Change to non-root user
USER raku
RUN curl --output pds-companion.zip -L 'https://github.com/moretrim/pds-companion/archive/0.2.0-alpha+20210317.zip' \
    && unzip pds-companion.zip                                                                                      \
    && zef install --/test Terminal::ANSIColor                                                                      \
    && cd pds-companion-*                                                                                           \
    && zef install --/test .

ENTRYPOINT ["bash", "-c"]
