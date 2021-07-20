FROM alpine:latest

# Environment Variables
ENV GODOT_VERSION "3.2.3"
ENV GODOT_EXPORT_PRESET="Linux/X11"
ENV GODOT_GAME_NAME ""
ENV HTTPS_GIT_REPO ""

# Updates and installs to the server
RUN apk update
RUN apk add --no-cache bash
RUN apk add --no-cache wget
RUN apk add --no-cache git

# Allow this to run Godot
RUN wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.31-r0/glibc-2.31-r0.apk
RUN apk add --allow-untrusted glibc-2.31-r0.apk

# Download Godot and export template, version is set from variables
RUN wget https://downloads.tuxfamily.org/godotengine/${GODOT_VERSION}/Godot_v${GODOT_VERSION}-stable_linux_headless.64.zip \
    && wget https://downloads.tuxfamily.org/godotengine/${GODOT_VERSION}/Godot_v${GODOT_VERSION}-stable_export_templates.tpz \
    && mkdir ~/.cache \
    && mkdir -p ~/.config/godot \
    && mkdir -p ~/.local/share/godot/templates/${GODOT_VERSION}.stable \
    && unzip Godot_v${GODOT_VERSION}-stable_linux_headless.64.zip \
    && mv Godot_v${GODOT_VERSION}-stable_linux_headless.64 /usr/local/bin/godot \
    && unzip Godot_v${GODOT_VERSION}-stable_export_templates.tpz \
    && mv templates/* ~/.local/share/godot/templates/${GODOT_VERSION}.stable \
    && rm -f Godot_v${GODOT_VERSION}-stable_export_templates.tpz Godot_v${GODOT_VERSION}-stable_linux_headless.64.zip

# Make needed directories for container
RUN mkdir /godotapp
RUN mkdir /godotbuildspace

# Move to the build space and export the .pck
WORKDIR /godotbuildspace
RUN git clone ${HTTPS_GIT_REPO} .
RUN godot --path /godotbuildspace --export-pack ${GODOT_EXPORT_PRESET} ${GODOT_GAME_NAME}.pck
RUN mv ${GODOT_GAME_NAME}.pck /godotapp/

# Change to the godotapp space, delete the source,  and run the app
WORKDIR /godotapp
run rm -f -R /godotbuildspace
CMD godot --main-pack ${GODOT_GAME_NAME}.pck