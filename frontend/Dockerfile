FROM node:lts-alpine

#RUN mkdir -p /frontend
# make the 'app' folder the current working directory
WORKDIR /frontend

# install simple http server for serving static content
RUN npm install -g @vue/cli



# add `/app/node_modules/.bin` to $PATH
ENV PATH /frontend/node_modules/.bin:$PATH

CMD [ "DIR"]
# copy both 'package.json' and 'package-lock.json' (if available)
COPY package.json ./package.json

COPY package-lock.json ./package-lock.json

# install project dependencies
RUN npm install

# copy project files and folders to the current working directory (i.e. 'app' folder)
COPY . .

RUN npm rebuild node-sass

# build app for production with minification
RUN npm run build

EXPOSE 8080
CMD ["npm", "run", "serve"]