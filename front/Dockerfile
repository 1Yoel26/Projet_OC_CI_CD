# 1 Build de l'app Angular pour pouvoir ensuite l'executer dans le navigateur correctement

FROM node:latest as BuildAppAngular
WORKDIR /usr/local/AppFront
COPY . .
RUN npm install
RUN npm run build


# 2 Lancement du serveur web Nginx en mode léger avec Alpine
#   afin de pouvoir faire après http://localhost:monAppAngular

# 2.1 Copie de l'app angular build, dans le dossier lisible par le serveur web nginx (pour qu'il puisse l'afficher)
FROM nginx:alpine
COPY --from=BuildAppAngular /usr/local/AppFront/dist/bobapp /usr/share/nginx/html

# indique pour docker que le port utilisé par nginx est le port 80 (http)
EXPOSE 80








#FROM node:latest as build

#WORKDIR /usr/local/app
#COPY ./ /usr/local/app/

#RUN yarn
#RUN npm run build
 
#FROM nginx:latest as production

#COPY nginx.conf /etc/nginx/conf.d/default.conf
#COPY --from=build /usr/local/app/dist/bobapp /usr/share/nginx/html

#EXPOSE 80