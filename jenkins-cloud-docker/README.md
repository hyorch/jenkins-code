# Jenkins Cloud Docker
Using Docker as Cloud for Jenknins.

1. Get Docker group id in the host running Docker.
2. Build Jenkins image adding a group called **docker** with same group id.
3. Add Cloud with type Docker.
4. Set connection to **unix:///var/run/docker.sock**