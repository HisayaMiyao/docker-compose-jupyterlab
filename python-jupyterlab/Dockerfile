FROM ubuntu:18.04



RUN apt-get update && \
    apt-get install -y software-properties-common \
                       tzdata

RUN apt-add-repository -y ppa:git-core/ppa && \
    apt-get update && \
    apt-get install -y git \
                       vim



RUN git clone https://github.com/pyenv/pyenv.git ~/.pyenv
RUN echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc && \
    echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc

RUN echo 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.bashrc

RUN apt-get install -y make build-essential libssl-dev zlib1g-dev \
                       libbz2-dev libreadline-dev libsqlite3-dev wget \
                       curl llvm libncurses5-dev xz-utils tk-dev \
                       libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev

ENV PATH $PATH:/root/.pyenv/bin


RUN pyenv install 3.6.5 && \
    pyenv global 3.6.5 && \
    pyenv rehash

ENV PATH $PATH:/root/.pyenv/shims

RUN pip install --upgrade pip && \
    pip install jupyterlab

RUN mkdir /home/project
# COPY requirements.txt .

# RUN pip install -r requirements.txt --no-cache-dir

RUN pip install ipywidgets