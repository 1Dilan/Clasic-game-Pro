# Frontend Dockerfile
FROM node:18

# Instalar dependencias necesarias para React Native
RUN apt-get update && apt-get install -y \
    adb \
    android-tools-adb \
    openjdk-11-jdk \
    wget \
    unzip \
    git

# Configurar variables de entorno para Android
ENV ANDROID_HOME /opt/android-sdk
ENV PATH ${PATH}:${ANDROID_HOME}/tools:${ANDROID_HOME}/platform-tools

# Descargar Android SDK
RUN mkdir -p ${ANDROID_HOME} && cd ${ANDROID_HOME} \
    && wget https://dl.google.com/android/repository/commandlinetools-linux-8092744_latest.zip \
    && unzip commandlinetools-linux-*_latest.zip \
    && rm commandlinetools-linux-*_latest.zip \
    && mkdir -p ${ANDROID_HOME}/cmdline-tools/latest \
    && mv ${ANDROID_HOME}/cmdline-tools/* ${ANDROID_HOME}/cmdline-tools/latest/ \
    && ln -s ${ANDROID_HOME}/cmdline-tools/latest/bin/* /usr/local/bin

# Aceptar licencias y instalar paquetes necesarios
RUN yes | sdkmanager --licenses \
    && sdkmanager "platform-tools" "platforms;android-33" "build-tools;33.0.0"

# Crear directorio de trabajo
WORKDIR /app

# Instalar React Native CLI globalmente
RUN npm install -g react-native-cli

# Copiar package.json y package-lock.json (si existen)
COPY package*.json ./

# Instalar dependencias del proyecto
RUN npm install

# Copiar el resto del código fuente
COPY . .

# Exponer el puerto para Metro bundler
EXPOSE 8081

# Comando por defecto
CMD ["npm", "start"]