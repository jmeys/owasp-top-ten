FROM node:10 as installer
COPY . /owasp-top-ten-ppt
WORKDIR /owasp-top-ten-ppt
RUN npm install

FROM node:10-alpine
WORKDIR /owasp-top-ten-ppt
COPY --from=installer /owasp-top-ten-ppt .
RUN addgroup juicer && \
    adduser -D -G juicer juicer && \
    chown -R juicer /owasp-top-ten-ppt && \
    chgrp -R 0 /owasp-top-ten-ppt/ && \
    chmod -R g=u /owasp-top-ten-ppt/
USER juicer
EXPOSE  8000
CMD ["npm", "start"]