FROM node:10 as installer
COPY . /owasp-top-ten-ppt
WORKDIR /owasp-top-ten-ppt
RUN npm install --production --unsafe-perm
RUN rm -rf frontend/node_modules

FROM node:10-alpine
ARG BUILD_DATE
ARG VCS_REF
WORKDIR /owasp-top-ten-ppt
COPY --from=installer /owasp-top-ten-ppt .
EXPOSE  8000
CMD ["npm", "start"]