FROM node:4.3
MAINTAINER Medici.Yan@Gmail.com
ENV LC_ALL C.UTF-8
ENV TZ=Asia/Shanghai

RUN set -ex; \
  ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone; \
  mkdir -p /htdocs

COPY . /htdocs/
WORKDIR /htdocs/

RUN set -ex; \
  npm --registry=https://registry.npmmirror.com install

ENV PORT=3000 \
  ANT_MONGO_URI=mongodb://127.0.0.1/ant \
  ANT_MAIL_NAME='ANT' \
  ANT_MAIL_HOST='smtp.qq.com' \
  ANT_MAIL_PORT=465 \
  ANT_MAIL_SECURE=true \
  ANT_MAIL_EMAIL='email@user.com' \
  ANT_MAIL_PASSWORD='email-password'

EXPOSE 3000
ENTRYPOINT ["/bin/bash", "/htdocs/start.sh"]
CMD ["tail", "-f", "/dev/null"]
