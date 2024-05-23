



If `slapd` won't start at boot, then you should probably edit `/usr/local/etc/rc.d/slapd` and add the option `NETWORKING` to the line that says `# REQUIRE: FILESYSTEMS ldconfig`.
