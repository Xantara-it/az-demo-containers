FROM postgres:15.2

ARG CHECKMK_URL
ARG CHECKMK_USER
ARG CHECKMK_PASS
RUN apt update && \
    apt install -y curl xinetd && \
    curl -L \
      -H "Authorization: Bearer $CHECKMK_USER $CHECKMK_PASS" \
      -o checkmk-agent.deb \
      "$CHECKMK_URL/check_mk/api/1.0/domain-types/agent/actions/download_by_host/invoke?os_type=linux_deb&agent_type=generic" && \
    ls -l && \
    apt install -y ./checkmk-agent.deb
