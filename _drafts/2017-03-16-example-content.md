---
layout: post
title: "Example Content"
author: "Chester"
tags:
- default
gallery: true
math: true
other_image_sources:
- 2018-04-09-chocolate-crinkles
---

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas tincidunt ornare nibh, non elementum augue tempus eget. Pellentesque tempus scelerisque iaculis. Nullam interdum ultricies nibh quis sollicitudin. Donec ornare fermentum facilisis. Ut at sem ac sem imperdiet varius a eget tortor. Nam eu augue eget orci semper maximus in eget augue. Mauris ornare, nisl ut suscipit consectetur, mi quam interdum tellus, at rutrum quam eros ultrices mi.

# Headers
{% highlight markdown %}
# H1
## H2
### H3
#### H4
##### H5
###### H6
{% endhighlight %}

# H1
## H2
### H3
#### H4
##### H5
###### H6

# Text formatting
{% highlight markdown %}
- **Bold**
- _Italics_
- ~~Strikethrough~~
- <ins>Underline</ins>
- <sup>Superscript</sup>
- <sub>Subscript</sub>
- Abbreviation: <abbr title="HyperText Markup Language">HTML</abbr>
- Citation: <cite>&mdash; Chester How</cite>
{% endhighlight %}

- **Bold**
- _Italics_
- ~~Strikethrough~~
- <ins>Underline</ins>
- <sup>Superscript</sup>
- <sub>Subscript</sub>
- Abbreviation: <abbr title="HyperText Markup Language">HTML</abbr>
- Citation: <cite>&mdash; Chester How</cite>

# Lists
{% highlight markdown %}
1. Ordered list item 1
2. Ordered list item 2
3. Ordered list item 3

* Unordered list item 1
* Unordered list item 2
* Unordered list item 3
{% endhighlight %}

1. Ordered list item 1
2. Ordered list item 2
3. Ordered list item 3

* Unordered list item 1
* Unordered list item 2
* Unordered list item 3

# Links
{% highlight markdown %}
Check out tale on [GitHub](https://github.com/chesterhow/tale).
{% endhighlight %}

Check out tale on [GitHub](https://github.com/chesterhow/tale).

# Images
{% highlight markdown %}
![Placeholder image](https://placehold.it/800x400 "Placeholder image")

![Image with caption](https://placehold.it/700x400 "Image with caption")
_This is an image with a caption_

![Local image]({{ "/assets/img/thumbnail/2018-04-09-chocolate-crinkles-1_thumb_800.jpg" | absolute_url }} "mouseover")_caption_
{% endhighlight %}


![Placeholder image](https://placehold.it/800x400 "Placeholder image")

![Image with caption](https://placehold.it/700x400 "Image with caption")
_This is an image with a caption_

![Local image]({{ "/assets/img/thumbnail/2018-04-09-chocolate-crinkles-1_thumb_800.jpg" | absolute_url }} "mouseover")_caption_

# Image Galleries

{% highlight html %}
<div class="gallery">
  <figure name="1" alt="Image description" caption="caption 1"></figure>
  <figure name="2018-04-09-chocolate-crinkles-1" alt="Image description" caption="caption 2"></figure>
</div>
{% endhighlight %}

<div class="gallery">
  <figure name="1" alt="Image description" caption="caption 1"></figure>
  <!-- <figure name="2018-04-09-chocolate-crinkles-1" alt="Image description" caption="caption 2"></figure> -->
</div>

# Code and Syntax Highlighting
Use back-ticks for `inline code`. Multi-line code snippets are supported too through Pygments.

{% highlight js %}
// Sample javascript code
var s = "JavaScript syntax highlighting";
alert(s);
{% endhighlight %}

{% highlight python %}
# Sample python code
s = "Python syntax highlighting"
print s
{% endhighlight %}

Adding `linenos` to the Pygments tag enables line numbers.

{% highlight js  linenos %}
// Sample javascript code
var s = "JavaScript syntax highlighting";
alert(s);
{% endhighlight %}

# Blockquotes
{% highlight markdown %}
> Curabitur blandit tempus porttitor. Nullam quis risus eget urna mollis ornare vel eu leo. Nullam id dolor id nibh ultricies vehicula ut id elit.

{% endhighlight %}

> Curabitur blandit tempus porttitor. Nullam quis risus eget urna mollis ornare vel eu leo. Nullam id dolor id nibh ultricies vehicula ut id elit.

# Horizontal Rule & Line Break
{% highlight markdown %}
Use `<hr>` for horizontal rules

<hr>

and `<br>` for line breaks.

<br>
{% endhighlight %}

Use `<hr>` for horizontal rules

<hr>

and `<br>` for line breaks.

<br>

GIST

<script src="https://gist.github.com/rishabmps/36fef4c3e1750890ef18fa27a2e4099f.js"></script>

{% highlight matlab  linenos %}
// Sample javascript code
x = -1:.1:1;
y = -1:.1:1;
[Xm, Ym] = meshgrid(x,y);
Lm = Xm.^2 - Ym.^2;
hdl = surf(Xm, Ym, Lm);
{% endhighlight %}

## MATHS

$$% <![CDATA[
\begin{aligned}
V_*(s) &= \max_{a \in \mathcal{A}} Q_*(s,a)\\
\quad Q_*(s, a) &= R(s, a) + \gamma \sum_{s' \in \mathcal{S}} P_{ss'}^a V_*(s') \\
\quad \quad V_*(s) &= \max_{a \in \mathcal{A}} \big( R(s, a) + \gamma \sum_{s' \in \mathcal{S}} P_{ss'}^a V_*(s') \big) \\
Q_*(s, a) &= R(s, a) + \gamma \sum_{s' \in \mathcal{S}} P_{ss'}^a \max_{a' \in \mathcal{A}} Q_*(s', a')
\end{aligned} %]]>$$

## ALGORITHMS

<pre class="algorithm" style="display:none">
    \begin{algorithm}
    \caption{Test text-style}
    \begin{algorithmic}
    \REQUIRE some preconditions
    \ENSURE some postconditions
    \INPUT some inputs
    \OUTPUT some outputs
    \PROCEDURE{Test-Declarations}{}
        \STATE font families: {\sffamily sffamily, \ttfamily ttfamily, \normalfont normalfont, \rmfamily rmfamily.}
        \STATE font weights: {normal weight, \bfseries bold, \mdseries 
        medium, \lfseries lighter. }
        \STATE font shapes: {\itshape itshape \scshape Small-Caps \slshape slshape \upshape upshape.}
        \STATE font sizings:  \tiny tiny \scriptsize scriptsize \footnotesize
        footnotesize \small small \normalsize normal \large large \Large Large
        \LARGE LARGE \huge huge \Huge Huge \normalsize
    \ENDPROCEDURE
    \PROCEDURE{Test-Commands}{}
        \STATE \textnormal{textnormal,} \textrm{textrm,} \textsf{textsf,} \texttt{texttt.}
        \STATE \textbf{textbf,} \textmd{textmd,} \textlf{textlf.}
        \STATE \textup{textup,} \textit{textit,} \textsc{textsc,} \textsl{textsl.}
        \STATE \uppercase{uppercase,} \lowercase{LOWERCASE.}
    \ENDPROCEDURE
    \PROCEDURE{Test-Colors}{}
    % feature not implemented
    \ENDPROCEDURE
    \end{algorithmic}
    \end{algorithm}

    \begin{algorithm}
    \caption{Test atoms}
    \begin{algorithmic}
    \STATE \textbf{Specials:} \{ \} \$ \& \# \% \_
    \STATE \textbf{Bools:} \AND \OR \NOT \TRUE \FALSE
    \STATE \textbf{Carriage return:} first line \\ second line
    \STATE \textbf{Text-symbols:} \textbackslash
    \STATE \textbf{Quote-symbols:} `single quotes', ``double quotes''
    \STATE \textbf{Math:} $(\mathcal{C}_m)$, $i \gets i + 1$, $E=mc^2$, \( x^n + y^n = z^n \), $\$$, \(\$\)
    \END{ALGORITHMIC}
    \END{ALGORITHM}
</pre>
<pre class="algorithm" style="display:none">
        \begin{algorithm}
        \caption{Test control blocks}
        \begin{algorithmic}
        \PROCEDURE{Test-If}{}
            \IF{&lt;cond&gt;}
                \STATE &lt;block&gt;
            \ELIF{&lt;cond&gt;}
                \STATE &lt;block&gt;
            \ELSE
                \STATE &lt;block&gt;
            \ENDIF
        \ENDPROCEDURE
        \PROCEDURE{Test-For}{$n$}
            \STATE $i \gets 0$
            \FOR{$i < n$}
                \PRINT $i$
                \STATE $i \gets i + 1$
            \ENDFOR
        \ENDPROCEDURE
        \PROCEDURE{Test-For-All}{$n$}
            \FORALL{$i \in \{0, 1, \cdots, n\}$}
                \PRINT $i$
            \ENDFOR
        \ENDPROCEDURE
        \PROCEDURE{Test-While}{$n$}
            \STATE $i \gets 0$
            \WHILE{$i < n$}
                \PRINT $i$
                \STATE $i \gets i + 1$
            \ENDWHILE
        \ENDPROCEDURE
        \PROCEDURE{Test-Repeat}{$n$}
            \STATE $i \gets 0$
            \REPEAT
                \PRINT $i$
                \STATE $i \gets i + 1$
            \UNTIL{$i>n$}
        \ENDPROCEDURE
        \end{algorithmic}
        \end{algorithm}
        \begin{algorithm}
        \caption{Test statements and comments}
        \begin{algorithmic}
        \PROCEDURE{Test-Statements}{}
            \STATE This line is a normal statement
            \PRINT \texttt{`this is print statement'}
            \RETURN $retval$
        \ENDPROCEDURE

        \PROCEDURE{Test-Comments}{} \COMMENT{comment for procedure}
            \STATE a statement \COMMENT{inline comment}
            \STATE \COMMENT{line comment}
            \IF{some condition}\COMMENT{comment for if}
                \RETURN \TRUE \COMMENT{another inline comment}
            \ELSE \COMMENT{comment for else}
                \RETURN \FALSE \COMMENT{yet another inline comment}
            \ENDIF
        \ENDPROCEDURE
        \end{algorithmic}
        \end{algorithm}
</pre>
<pre class="algorithm" style="display:none">
        % This quicksort algorithm is extracted from Chapter 7, Introduction 
        % to Algorithms (3rd edition)
        \begin{algorithm}
        \caption{Quicksort}
        \begin{algorithmic}
        \PROCEDURE{Quicksort}{$A, p, r$}
            \IF{$p < r$} 
                \STATE $q = $ \CALL{Partition}{$A, p, r$}
                \STATE \CALL{Quicksort}{$A, p, q - 1$}
                \STATE \CALL{Quicksort}{$A, q + 1, r$}
            \ENDIF
        \ENDPROCEDURE
        \PROCEDURE{Partition}{$A, p, r$}
            \STATE $x = A[r]$
            \STATE $i = p - 1$
            \FOR{$j = p$ \TO $r - 1$}
                \IF{$A[j] < x$}
                    \STATE $i = i + 1$
                    \STATE exchange
                    $A[i]$ with     $A[j]$
                \ENDIF
                \STATE exchange $A[i]$ with $A[r]$
            \ENDFOR
        \ENDPROCEDURE
        \end{algorithmic}
        \end{algorithm}
</pre>

_The end_
