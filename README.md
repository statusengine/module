# Statusengine Broker Module
The Statusengine Broker Module is a small C binary that gets loaded into your Naemon or Nagios Core.

It will grab all status and configuration information, encode them as JSON, and put them into the Gearman Job Server.
Due to the queuing engine (Gearman) your Monitoring Core will not get blocked by an slow database or disk io issues.
It is highly recommended to run the Gearman Job Server on the same node as the monitoring core.

Visit the [documentation](https://statusengine.org/) for more information about Statusengine Broker Module

## Install
````
apt-get install gearman-job-server libgearman-dev gearman-tools uuid-dev libjson-c-dev manpages-dev build-essential libglib2.0-dev
git clone https://github.com/statusengine/module.git
cd module/
make all
````

## Load the broker
````
broker_module=/opt/statusengine/module/statusengine-naemon-1-0-5.o
````

# License
GNU General Public License Version 2
````
Statusengine Broker Module
Copyright (c) 2014 - present Daniel Ziegler <daniel@statusengine.org>

This program is free software; you can redistribute it and/or
modify it under the terms of the GNU General Public License
as published by the Free Software Foundation in version 2

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software
Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.
````
