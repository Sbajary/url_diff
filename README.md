url_diff
========

A tool (like diff) to show the differences between 2 URLs.

In my job I work with a lot of URLs, and often need to know which parameters (names and/or values) differ between 2.  I got fed up with "eye-balling" URLs to figure out the difference (esp. with different param orderings) so I'm developing a tool to do it for me.

enter url_diff
--------------

for example, what's different between these 2 URLs:
`http://example.com/?foo=bar&cake=lie&you=monster&beer=good&speech=free&breaking=bad`
`http://example.com/?&speech=free&beer=good&aperture=science&foo=bar&you=here&breaking=over`

    url_diff.py 'http://example.com/?foo=bar&cake=lie&you=monster&beer=good&speech=free&breaking=bad' \
      'http://example.com/?&speech=free&beer=good&aperture=science&foo=bar&you=here&breaking=over'
    breaking
    < bad
    > over

    cake
    < lie

    you
    < monster
    > here

    aperture
    > science


I think the help message explains the rest:

    python url_diff.py --help
    usage: url_diff.py [-h] [--hostname] [--names] <left URL> <right URL>

    show the difference between 2 urls. Inspired by the unix utility diff

    positional arguments:
      <left URL>   URL to diff against. Logically handled as the left argurmnt of diff.
      <right URL>  URL to diff against. Logically handled as the right argurmnt of diff.

    optional arguments:
      -h, --help   show this help message and exit
      --hostname   also diff URL hostname
      --names, -n  only diff URL parameter names.

    Currenty this tool discards everything after # if present.
    See https://github.com/google/url_diff for more information.

Also, please keep in mind this is still in alpha, and it's currently a weekend project. Hope y'all find it useful too.
