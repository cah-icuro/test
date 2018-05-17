
# The Painting Problem

A painter has three different types of paint: Quartz, Amethyst, and Jade.  This painter will be painting a sequence of strokes, and your goal is to tell us what the final painting looks like.  It seems simple; however, these paints mix in mysterious ways...

Quartz paint is relatively clear in color and non-interactive, so when it mixes with another type of paint, it leaves the other unaffected.  For example, Quartz + Jade yields Jade.  It also has the same behaviour towards itself, so Quartz + Quartz yields Quartz.

Amethyst and Jade are more unusual.  When mixed with each other, they yield Quartz; when painted over themselves, Jade and Amethyst yield Amethyst and Jade, respectively.  Thus, Jade on Jade yields Amethyst, while Amethyst on Amethyst yields Jade.

To keep things simple, the painter will be painting on a number strip, viz. a number line with some height (so he has a surface on which to paint).  He will paint a sequence of strokes, starting and ending at integer points along this number strip.  Note that not all strokes may be in the same direction.  You must then determine the end result, given the sequence of strokes painted.

<br/>

## Input

Your solution function will have the signature:

`void painting_solution(std::vector<stroke> &strokes, std::vector<unsigned char> &results);`

where the data type `stroke` is defined as the following struct:

```
struct stroke {
  int start;
  int end;
  unsigned char color;
};
```

The first parameter, `std::vector<stroke> &strokes`, is the input to your algorithm.  It represents the sequence of strokes that the painter will carry out.  For each stroke, the `start` integer tells you the position on the number strip where the painter will start this stroke, the `end` integer tells you the position on the number strip where the painter will finish this stroke, and the `color` character tells you which paint the painter will use for this stroke.  The `color` character will be one of `'q'`, `'a'`, or `'j'`, representing Quartz, Amethyst, or Jade, respectively.

<br/>

## Output

The output of your algorithm should be stored in the second parameter of your solution function.  Once again, the solution function has the form:

`void painting_solution(std::vector<stroke> &strokes, std::vector<unsigned char> &results);`

The results vector describes the final paint colors in the number strip.  If `left_endpoint` is the minimum-valued endpoint of all the strokes and `right_endpoint` is the maximum-valued such endpoint, then the array will have length `right_endpoint - left_endpoint`.  Each element in the array contains a character representing the paint color within one unit block on the number strip (using the same color character values as in the input strokes), where the first element in the array represents the leftmost unit block painted and the last element represents the rightmost unit block painted.

If the `strokes` vector is empty or if no non-zero-length strokes were made, simply output an empty vector.

<br/>

## Simple Example

Suppose the painter paints a stroke of Jade from 1 to 3, a stroke of Amethyst from 2 to 4, and then a Stroke of Jade from 1 to 2.  The input would be:

```
stroke{1, 3, 'j'},
stroke{2, 4, 'a'},
stroke{1, 2, 'j'}
```

Our results array will have length 4 - 1 = 3, with the first element of the array representing the integer block [1, 2] and the last element of the array representing the integer block [3, 4].  The final colors in each block will be:

```
[1, 2]: Amethyst
[2, 3]: Quartz
[3, 4]: Amethyst
```

Thus, when `painting_solution` returns, its `results` vector should contain precisely three characters: `{'a', 'q', 'a'}`.
