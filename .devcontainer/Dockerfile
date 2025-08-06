FROM ocurrent/opam-staging:oxcaml

ARG USERNAME=codespace
ARG USER_UID=1000
ARG USER_GID=$USER_UID

USER ${USERNAME}

# CR mshinwell/avsm: use a hash for --repos, but will need to restore the
# URL afterwards for any user opam update commands.

RUN eval $(opam env --switch 5.2.0+ox) && \
        opam install -j 1  --yes ocamlformat && \
        opam clean

RUN df -h

RUN eval $(opam env --switch 5.2.0+ox) && \        
        opam install -j 1 --yes merlin && \
        opam clean

RUN df -h

RUN eval $(opam env --switch 5.2.0+ox) && \          
        opam install -j 1  --yes async && \
        opam clean

RUN df -h

RUN eval $(opam env --switch 5.2.0+ox) && \          
        opam install -j 1  --yes ocaml-lsp-server && \
        opam clean

RUN df -h

RUN eval $(opam env --switch 5.2.0+ox) && \
        opam install --yes utop && \
        opam install --yes parallel && \
        opam install --yes core_unix

USER root
