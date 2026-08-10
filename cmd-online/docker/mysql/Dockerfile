FROM mysql:8.4

COPY docker/mysql/01-create-bitrix-user.sh /docker-entrypoint-initdb.d/01-create-bitrix-user.sh
RUN chmod +x /docker-entrypoint-initdb.d/01-create-bitrix-user.sh