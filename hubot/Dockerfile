FROM repo.coloseo.io/node:6.5.0-dev

COPY .npmrc /root/

RUN npm install -g hubot coffee-script yo generator-hubot && \
 rm -rf ~/.npm && \
 npm cache clear
