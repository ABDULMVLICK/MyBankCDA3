FROM node:20-alpine

WORKDIR /app

# Copier et installer les dépendances
COPY package.json package-lock.json ./
RUN npm ci

# Copier le reste du projet
COPY . .

EXPOSE 3000

CMD ["npm", "run", "dev", "--", "--host", "0.0.0.0", "--port", "3000"]
