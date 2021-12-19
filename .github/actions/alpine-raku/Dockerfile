FROM jjmerelo/alpine-raku:latest

USER root
RUN ["apk", "add", "--no-cache", "bash" \
    # workaround for https://github.com/JJ/alpine-raku/issues/24
    , "curl", "zef"]

USER raku
