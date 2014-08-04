#JSON::Jansson

This is a basic Perl 6 binding to libjansson: a C library for manipulating JSON data.

Still pretty rough! While JSON objects attempt to emulate P6 hashes or arrays, they don't have all the same capabilities.  In particular, assignment/building up new objects and consuming P6 types into JSON are not yet implemented.

JSON::Jansson is an appropriate choice if you're willing to trade features for speed. While JSON::Tiny is much more flexible and powerful, JSON::Jansson is (comparatively) blindingly fast.

How fast is that? `example/big.json` is approximately 10mb, generated by [json-generator](json-generator.com).  JSON::Jansson parsed it in about 2 seconds, while JSON::Tiny took a little over four minutes. NB: The usual disclaimers about lies and benchmarks apply -- this was an ad-hoc comparison run off a busy laptop.


### SYNOPSIS

    use JSON::Jansson;
    my $object = JSON.new('{"foo": 42}');
    say $object<foo>; # 42
    say $object.type; # (Hash)

    say $object.keys; # "foo"
    say $object.values; # 42
    say $object.kv; # "foo" 42

    my $array = JSON.new('["quux", 4, true]');
    say $array[0]; # "quux"
    say $array[0 .. 1]; #"quux", 4

### TODO

0. encoding p6 data structures into libjansson JSON objects
1. manipulate JSON as a p6 data structure (partly done, needs ^ for assignment)
2. don't leak memory (decref JSON pieces that are removed)
3. option to copy all the data out of jansson land into p6 structures, rather
than manipulating jansson JSON objects via p6.
4. tests

### LICENSE

Artistic License 2.0

### CREDITS

The wonderful NativeCall module, and FROGGS/timotimo for answering some
questions on #perl6.

### SEE ALSO

[JSON::Tiny](github.com/moritz/json)
