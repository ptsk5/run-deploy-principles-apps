FROM registry.access.redhat.com/ubi8/nodejs-14:1-51 as build

WORKDIR /app

USER 1001 

RUN chgrp -R 0 /app && \
    chmod -R g=u /app

COPY package*.json ./
# RUN npm install
RUN npm ci --only=production

COPY . . 
RUN npm run build


FROM registry.access.redhat.com/ubi8/nginx-120:1-5

COPY --from=build /app/build .
COPY --from=build /app/nginx/api-location.conf /opt/app-root/etc/nginx.default.d/

EXPOSE 8080 

CMD ["nginx", "-g", "daemon off;"]