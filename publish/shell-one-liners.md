# Shell One-Liners
###### shell, perl

See also <http://www.commandlinefu.com>.

## Various

* compute strings' SHA1 message digests

        $ for name in "jano" "fero" "daniel"; do echo -n $name | sha1sum; done
        b07fe6fe542d2d3b400e59b6e08eab04901148be  -
        792615d815e90d6fdd35e5916b2ce5a8014bd4e1  -
        3d0f3b9ddcacec30c4008c5e030e6c13a478cb4f  -

* find and rename multiple files (`*.log` => `*.LOG`)

        $ find . -type f -name '*.log ' | grep -v .do-not-touch | while read fname
        > do
        > echo mv $fname ${fname/.log/.LOG/}
        > done

### Search inside files 

E.g. search MS Word files for "robot" string:

    find /data -type f -iname "*.doc" -print0 | xargs -0 strings -f |  grep -i 'robot' > find.out

* to get just the filenames

        cat find.out | cut -d: -f1 | sort | uniq

