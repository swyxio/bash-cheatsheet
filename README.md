# bash-cheatsheet

concrete examples of bash syntax for people too lazy to actually learn bash

## Basic

Arrays:

```bash
month=("Jan" "Feb" "Mar" "Apr" "May" "Jun" "Jul" "Aug" "Sep" "Oct" "Nov" "Dec")
echo ${month[3]} ## Apr
```

Curly braces:

```bash
## sequences
echo {0..2} ## 0 1 2
echo {2..0} ## 2 1 0
echo {6..0..2} ## 6 4 2 0

## permutations
echo {1..4}{1..4} ## 11 12 13 14 21 22 23 24 31 32 33 34 41 42 43 44
dec2bin=({0..1}{0..1}{0..1}{0..1}{0..1}{0..1}{0..1}{0..1})
echo ${dec2bin[25]} ## 00011001

## output grouping
echo "I found all these PNGs:"; find . -iname "*.png"; echo "Within this bunch of files:"; ls > PNGs.txt ## only output of last ls command
{ echo "I found all these PNGs:"; find . -iname "*.png"; echo "Within this bunch of files:"; ls; } > PNGs.txt  ## all output
```

For loops:

```bash
## run `convert` on all .jpg's and output .png's
for i in *.jpg; do convert $i ${i%jpg}png; done

## stub out markdown files with frontmatter
for i in {1..3}; do echo ---\\ntitle: test post ${i}\\ndate: "2019-02-0${i}"\\nspoiler: short spoiler ${i}.\\n---\\n\\n lorem ipsum ${i} > post${i}.md; done
```

modulus operators: at the end `%` and at start `#`:

```bash
i=image.jpg
convert $i ${i%jpg}png ## run `convert image.jpg image.png`

a="Hello World!"
echo Goodbye${a#Hello} ## Goodbye World!

for i in *.jpg; do convert $i ${i%jpg}png; done ## run `convert` on all .jpg's and output .png's
```

## Resources these are pulled from

- https://www.linux.com/blog/learn/2019/2/all-about-curly-braces-bash
