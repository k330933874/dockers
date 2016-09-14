FROM repo.coloseo.io/erlang

# Env
ENV REBAR_VERSION 3.3.1

RUN echo '@edge http://nl.alpinelinux.org/alpine/edge/main' >> /etc/apk/repositories \
    && echo '@community http://nl.alpinelinux.org/alpine/edge/community' >> /etc/apk/repositories \
    && apk update \
    && apk upgrade \
    && apk add git make wget ca-certificates

# Install rebar
RUN cd /tmp \
    && mkdir rebar-${REBAR_VERSION} \
    && cd rebar-${REBAR_VERSION} \
    && wget -cqO rebar3 https://github.com/erlang/rebar3/releases/download/${REBAR_VERSION}/rebar3 \
    && chmod +x rebar3 \
    && cp rebar3 /usr/bin/rebar3 \
    && cd / && rm -rf /tmp/rebar-${REBAR_VERSION}

RUN apk del wget ca-certificates \
    && rm -rf /var/cache/apk/*