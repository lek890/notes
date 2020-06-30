### check the process of ip without lsof

ss - ltnup 'sport = :4003'

### to check linux distribution

cat /etc/os-release

### for alpine linux

use apk for package management
use openrc for service management
https://www.cyberciti.biz/faq/how-to-enable-and-start-services-on-alpine-linux/

### user group management

list all user groups
getent group
also available in cat /etc/passwd

### user to process mapping :

ps u 1

### group management

groups // lists groups
groups <username>
