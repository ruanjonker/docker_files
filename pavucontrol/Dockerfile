# Run pavucontrol in a container
#
FROM debian:jessie

# Tell debconf to run in non-interactive mode
ENV DEBIAN_FRONTEND noninteractive

# Make sure the repository information is up to date
RUN apt-get update && apt-get install -y pavucontrol --no-install-recommends

# Start volume control
ENTRYPOINT ["pavucontrol"]
