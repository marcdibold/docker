FROM nordlevel/nginx:0.1.0

MAINTAINER Marc Dibold <dibold@nordlevel.com>

ENV NODE_VERSION 8.9.3-r0

# Install node
RUN apk update && apk upgrade && \
    apk add --no-cache nodejs=$NODE_VERSION

# Install yarn
RUN apk add --no-cache --virtual .yarn-deps curl gnupg && \
  curl -o- -L https://yarnpkg.com/install.sh | sh && \
  apk del .yarn-deps
ENV PATH /root/.yarn/bin:$PATH
