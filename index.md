# n-gram

```perl
use strict;
my %ngrams;
while(<>){
  chomp;
  $_=~s/[^A-Za-z0-9_\- ]//g;
  $_=~s/^ +| +$//g;
  my @words=split / +/, lc $_;
  for(my $length=1; $length<=@words; $length++){
    for(my $start=0; $start+$length-1<@words; $start++){
      my $ngram=join(' ', @words[$start..$start+$length-1]);
      $ngrams{$ngram}++;
    }
  }
}
for(sort {$ngrams{$b}<=>$ngrams{$a}} keys %ngrams){
  print $_, "\t", $ngrams{$_}, "\n";
}
```
