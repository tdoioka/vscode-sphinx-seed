FROM sphinxdoc/sphinx-latexpdf

RUN apt-get update \
 && apt-get install -y \
    # for plant uml
    curl \
    default-jre \
    graphviz \
    fonts-takao

# plantuml
RUN curl -L https://github.com/plantuml/plantuml/releases/download/v1.2022.13/plantuml.jar -o /usr/local/bin/plantuml.jar

RUN pip install \
    # for automation
    sphinx-autobuild \
    # for Block diag
    sphinxcontrib-actdiag \
    sphinxcontrib-blockdiag \
    sphinxcontrib-nwdiag \
    sphinxcontrib-seqdiag \
    # for plant uml
    sphinxcontrib-plantuml

