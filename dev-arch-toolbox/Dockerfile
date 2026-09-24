FROM quay.io/toolbx/arch-toolbox:latest
ENV NAME=dev-arch-toolbox
RUN pacman -Syu --noconfirm btrfs-progs cmake clang make ninja wild mold systemd \
  && pacman -Scc --noconfirm \
  && echo LC_ALL=en_US.UTF8 >> /etc/environment \
  && echo LANG=en_US >> /etc/environment \
  && echo LANGUAGE=en_US >> /etc/environment \
  && echo -e "Host *\n    IdentitiesOnly yes" > /etc/ssh/ssh_config.d/10-identities_only.conf
