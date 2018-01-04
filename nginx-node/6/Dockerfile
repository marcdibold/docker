FROM nordlevel/nginx:0.1.0

MAINTAINER Marc Dibold <dibold@nordlevel.com>

ENV NODE_VERSION=v6.12.3 NPM_VERSION=3

# Install node
RUN apk add --update git curl make gcc g++ python linux-headers libgcc libstdc++ binutils-gold && \
    curl -sSL https://nodejs.org/dist/${NODE_VERSION}/node-${NODE_VERSION}.tar.gz | tar -xz && \
    cd /node-${NODE_VERSION} && \
    ./configure --prefix=/usr --without-snapshot && \
    make -j$(grep -c ^processor /proc/cpuinfo 2>/dev/null || 1) && \
    make install && \
    cd / && \
    npm install -g npm@${NPM_VERSION} && \
    apk del gcc g++ linux-headers binutils-gold && \
    rm -rf /node-${NODE_VERSION} /usr/include \
    /usr/share/man /tmp/* /var/cache/apk/* /root/.npm /root/.node-gyp \
    /usr/lib/node_modules/npm/man /usr/lib/node_modules/npm/doc /usr/lib/node_modules/npm/html

# Install yarn
RUN apk add --no-cache --virtual .yarn-deps curl gnupg && \
  curl -o- -L https://yarnpkg.com/install.sh | sh && \
  apk del .yarn-deps
ENV PATH /root/.yarn/bin:$PATH

# Cleanup

RUN rm -rf /etc/ssl