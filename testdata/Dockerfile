# Minimal image used to dogfood the reusable docker workflow
# (.github/workflows/docker.yaml) from this very repo.
#
# Design goals:
#   * tiny + fast to build (alpine base, no package installs -> no DL3018 pin warnings);
#   * has an ENTRYPOINT so `docker run <img> <arg>` appends the arg to it, giving the
#     smoke test a clean, reliable path (no CMD[0] auto-prepend needed here).
#
# Smoke test (smoke-test-args: "/etc/pipeline-test") prints the marker file created
# below and exits 0, proving the built image runs end-to-end through the pipeline.
FROM alpine:3.22

LABEL org.opencontainers.image.title="github-actions pipeline self-test"
LABEL org.opencontainers.image.description="Minimal image to dogfood the reusable docker workflow (lint/scan/smoke/push)."
LABEL org.opencontainers.image.source="https://github.com/leonidgrishenkov/github-actions"

RUN echo "github-actions pipeline self-test ok" > /etc/pipeline-test

ENTRYPOINT ["cat"]
CMD ["/etc/pipeline-test"]
