FROM ocurrent/opam-staging:oxcaml

ARG USERNAME=codespace
ARG USER_UID=1000
ARG USER_GID=$USER_UID

USER ${USERNAME}

RUN apt-get update && \
        apt-get remove -y swig3.0 unixodbc-dev libpq-dev \
        default-libmysqlclient-dev libgdiplus jq python3-pip sqlite3 \
        libsqlite3-dev tk-dev uuid-dev clang lldb llvm gdb vim-doc xtail \
        libsecret-1-dev && \
        apt-get install -y imagemagick
        
# CR mshinwell/avsm: use a hash for --repos, but will need to restore the
# URL afterwards for any user opam update commands.

RUN opam install -j 1  --yes ocamlformat && \
        opam clean

RUN opam install -j 1 --yes merlin && \
        opam clean

RUN df -h

RUN opam install -j 1  --yes async && \
        opam clean

RUN df -h

RUN opam install -j 1  --yes ocaml-lsp-server && \
        opam clean

RUN df -h

RUN opam install --yes utop && \
        opam install --yes parallel && \
        opam install --yes core_unix

USER root
