ARG BASE_IMAGE=m1k1o/neko:base
FROM $BASE_IMAGE

#
# install latest jellyfin client
RUN set -eux; apt-get update; \
    wget -O /tmp/jellyfin.deb "$(wget -q "https://api.github.com/repos/jellyfin/jellyfin-media-player/releases/latest" -O - | grep '^"browser_download_url":\|amd64-bullseye.deb"$' | sed -E 's/.*"([^"]+)".*/\1/')"; \
    apt-get install -y --no-install-recommends /tmp/jellyfin.deb; \
    apt-get clean -y; \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/* /tmp/*;

#
# copy configuation files
COPY supervisord.conf /etc/neko/supervisord/jellyfin.conf
