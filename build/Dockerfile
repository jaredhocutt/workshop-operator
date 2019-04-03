FROM quay.io/operator-framework/ansible-operator:v0.5.0

USER root

# Install Helm client
RUN \
    curl https://storage.googleapis.com/kubernetes-helm/helm-v2.13.1-linux-amd64.tar.gz --output /tmp/helm.tar.gz \
    && tar zxvf /tmp/helm.tar.gz -C /tmp \
    && mv /tmp/linux-amd64/helm /usr/local/bin/helm \
    && chmod +x /usr/local/bin/helm \
    && rm -rf /tmp/helm.tar.gz /tmp/linux-amd64/helm

# Install Ansible module dependencies
RUN \
    pip --no-cache-dir --disable-pip-version-check install \
        pyhelm \
        grpcio

USER 1001

COPY roles/ ${HOME}/roles/
COPY playbooks/ ${HOME}/playbooks/
COPY watches.yaml ${HOME}/watches.yaml
