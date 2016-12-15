FROM mhart/alpine-node:7

ARG USER
ARG USER_ID

#==============================================================================
# OS Setup
#==============================================================================

# Locale
RUN apk --no-cache add bash curl-dev ruby-dev build-base sudo ruby ruby-io-console ruby-rdoc ruby-irb libffi-dev python git


#==============================================================================
# LAMP Setup
#==============================================================================

# add local user
#RUN useradd --shell /bin/bash -c "" -u ${USER_ID} -o -m ${USER}
RUN adduser -D -u ${USER_ID} ${USER}
RUN addgroup sudo
RUN adduser ${USER} sudo
RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

#==============================================================================
# Node
#==============================================================================
# Node modules
RUN npm install --global gulp
RUN npm install --global bower

#==============================================================================
# LOCAL TO THIS PROJECT
#==============================================================================
# Ruby
RUN gem install bundler
RUN gem install hologram

USER ${USER}

CMD ["tail","-f","/dev/null"]
