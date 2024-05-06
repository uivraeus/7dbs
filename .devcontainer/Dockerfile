FROM mcr.microsoft.com/devcontainers/javascript-node:1-20-bullseye

# [Optional] Uncomment this section to install additional OS packages.
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends postgresql-common \
    && /usr/share/postgresql-common/pgdg/apt.postgresql.org.sh -y \
    && apt-get update \
    && apt-get -y install --no-install-recommends postgresql-client-16 \
    && apt-get -y install --no-install-recommends redis-tools
    
RUN export DEBIAN_FRONTEND=noninteractive \
    && export MONGODB_TOOL_VER=mongodb-database-tools-debian11-x86_64-100.9.4 \
    && curl -s -o /tmp/${MONGODB_TOOL_VER}.deb https://fastdl.mongodb.org/tools/db/${MONGODB_TOOL_VER}.deb \
    && chmod o+r /tmp/${MONGODB_TOOL_VER}.deb \
    && apt-get -y install /tmp/${MONGODB_TOOL_VER}.deb \
    && rm -rf rm -rf /tmp/${MONGODB_TOOL_VER}.deb


# [Optional] Uncomment if you want to install an additional version of node using nvm
# ARG EXTRA_NODE_VERSION=10
# RUN su node -c "source /usr/local/share/nvm/nvm.sh && nvm install ${EXTRA_NODE_VERSION}"

# [Optional] Uncomment if you want to install more global node modules
# RUN su node -c "npm install -g <your-package-list-here>"
