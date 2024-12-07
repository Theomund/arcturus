# Arcturus - Hobbyist operating system written in Rust.
# Copyright (C) 2024 Theomund
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU Affero General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU Affero General Public License for more details.
#
# You should have received a copy of the GNU Affero General Public License
# along with this program. If not, see <https://www.gnu.org/licenses/>.

FROM quay.io/fedora/fedora:41
RUN dnf copr enable -y mczernek/vale
RUN dnf install -y \
    --repofrompath 'terra,https://repos.fyralabs.com/terra41' \
    --setopt='terra.gpgkey=https://repos.fyralabs.com/terra41/key.asc' \
    terra-release-41 \
    && dnf clean all
RUN dnf install -y \
    bash-completion-2.13 \
    edk2-ovmf-20241117 \
    gcc-14.2.1 \
    gdb-15.2 \
    git-2.47.1 \
    limine-8.6.0 \
    make-4.4.1 \
    qemu-system-x86-9.1.2 \
    vale-3.9.1 \
    xorriso-1.5.6 \
    && dnf clean all
RUN useradd -m developer
USER developer
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y --default-toolchain nightly-2024-12-06 --target x86_64-unknown-none
ENV PATH="$PATH:/home/developer/.cargo/bin"
