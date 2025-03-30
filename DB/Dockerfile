FROM postgres:17

COPY Escola.sql /docker-entrypoint-initdb.d/

ENV POSTGRES_DB=Escola
ENV POSTGRES_USER=unifaat
ENV POSTGRES_PASSWORD=unifaat

EXPOSE 5432
