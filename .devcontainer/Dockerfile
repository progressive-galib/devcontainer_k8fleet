FROM ocaml/opam:ubuntu-22.04

USER root

# Install system dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    git \
    wget \
    curl

USER opam

# Switch to non-interactive opam
ENV DEBIAN_FRONTEND=noninteractive

# Initialize opam
RUN opam init --yes --disable-sandboxing

# Install required OCaml packages
RUN eval $(opam env) && \
    opam install -y ocaml-lsp-server odoc ocamlformat utop dune

# Create a workspace directory
WORKDIR /home/opam/workspace

# Copy your project files (if any)
COPY . /home/opam/workspace

# Set the default command
CMD ["bash"]

