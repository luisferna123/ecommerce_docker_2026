FROM eclipse-temurin:17-jdk-jammy

# configuracion de la aplicaación
ENV APP_HOME=/ecommerce-app
RUN mkdir -p $APP_HOME
WORKDIR $APP_HOME

# Puerto que voy a exponer
EXPOSE 8084

# Copiar el JAR generdo por MAVEN (nombre fijo de la version)
COPY target/ecommerce-*.jar app.jar

#Usuario no-root para seguridad
RUN useradd -m appuser && chown -R appuser:appuser $APP_HOME
USER appuser

# Salud del sistema interno
HEALTHCHECK --interval=30s --timeout=3s \
    CMD curl -f http://localhost:8084/actuactor/healt || exit 1

# Comando de ejecucion
ENTRYPOINT ["java", "-jar", "app.jar"]