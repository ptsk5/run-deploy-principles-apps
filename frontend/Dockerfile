FROM registry.access.redhat.com/ubi8/nodejs-14:1-51 as build

COPY package*.json .

RUN npm ci --only=production

COPY . . 
RUN npm run build


FROM registry.access.redhat.com/ubi8/nginx-120:1-5

COPY --from=build /usr/src/app/build .
COPY --from=build /usr/src/app/nginx/api-location.conf /opt/app-root/etc/nginx.default.d/

EXPOSE 8080 

CMD ["nginx", "-g", "daemon off;"]