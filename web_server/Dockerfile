FROM node:latest
WORKDIR /app
COPY . .
# Install newman-reporter-csv globally
RUN cd /go/src/app/go-rest-web/react-todo && \
    npm install @tanstack/react-query@4.28.0 \
    @tanstack/react-query-devtools@4.28.0 \
    zustand@4.3.6 \
    @heroicons/react@2.0.16 \
    react-router-dom@6.10.0 \
    axios@1.3.4 \
    -D tailwindcss