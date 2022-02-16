---
layout: post
title: "Simple fractal"
date: 2022-02-10
categories: python, numpy, PIL, fractals
usemathjax: true
---

# Visualize the Mandelbrot Set

Sometime ago I read [Chaos: Making a New Science](https://en.wikipedia.org/wiki/Chaos:_Making_a_New_Science) by James Gleick. Very cool book. And ever since then I've been interested in [fractals](https://en.wikipedia.org/wiki/Fractal). One of my favorite youtube channels, [Numberphile](https://www.numberphile.com/), has several videos on fractals and the Mandelbrot Set in particular:
- [What's special about the Mandelbrot Set?](https://www.numberphile.com/videos/whats-special-about-the-mandelbrot-set?rq=mandelbrot)
- [Fibonacci and Mandelbrot](https://www.numberphile.com/videos/fibonacci-and-mandelbrot?rq=mandelbrot)

In 2021 I was working with NumPy on a side-project. I had done some work with [Pillow](https://pillow.readthedocs.io/en/stable/) and I wondered if I could use NumPy and Pillow to produce a simple visualization of the Mandelbrot Set. I decided to check the Wikipedia page on the [Mandelbrot Set](https://en.wikipedia.org/wiki/Mandelbrot_set) to see how it's defined mathmatically.

$$ f_c(z) = z^{2} + c$$

This equation states to square a number $$z$$ and then add some constant $$c$$. What happens if you treat the output of one operation as the input to the next? So, for intial values of $$z = 1$$ and $$c = 2$$, the output is 3. Feeding this new value of $$z$$ into the equation and keeping $$c = 2$$ produces 11. Repeating this process and the values quickly diverge to infinity. Setting the values $$z = 1$$ and $$c = -1$$ and the process alternates between $$0$$ and $$-1$$. Setting $$z = 1.6$$ and $$c = -1$$ and the process eventually alternates between $$0$$ and $$-1$$. Setting $$z = 1.7$$ and $$c = -1$$ and the process diverges to infinity. What are the bounds of $$z$$ and $$c$$ such that $$z$$ and $$c$$ do not diverge to infinity? What if $$c$$ is allowed to include imaginary numbers such as $$2 - 8i$$, what are those bounds? Visualizing when a set of initial values diverge or do not diverge to infinity is the Mandelbrot set.

This is a relatively simple operation. We can use NumPy (because it can work with [complex](https://numpy.org/doc/stable/reference/generated/numpy.imag.html) numbers) to produce the values in the Mandelbrot Set and Pillow to produce the visualization. This short tutorial produces the VERY SIMPLE black and white visualization of the Mandelbrot set as seen below:

<img src="https://raw.githubusercontent.com/mike-babb/simple_fractal/main/simple_fractal_bw.bmp" alt="Mandelbrot Set" width="250"/>

(Note that this image has been reduced. The size of the image produced by the Jupyter Notebook is 1000x1000.)

There are two parts to producing this graphic. This first part is a function that evaluates a combination of $$z$$ and $$c$$ to see if it diverges to infinity. This function returns $$1$$ if the initial values diverge or $$0$$ if the initial values do not diverge.

```python
# define a function that evaluates z = z^2 + c
def iteration_function(z, c, n, display_value = False):    
    """ EVALUATE z = z^2 + c n times. If after n trials z is less than 100, 
    assume that z does not diverge to infinity.
    z: real number
    c: complex number
    n: number of iterations to check
    display_value: boolean: Switch to print the current value
    """
    i = 0
    # set the outcome to zero, meaning it does not diverge
    outcome = 0    
    while i <= n and outcome == 0:        
        
        z = z**2 + c
        i += 1
        if display_value:
            print(z)
        if np.isfinite(z):
            real_part = abs(np.real(z))
            imag_part = abs(np.imag(z))
            
            if real_part > 10 or imag_part > 10:
                outcome = 1            
        else:
            outcome = 1
    # return the outcome and the number of iterations it took to crest 100
    return (outcome, i)          
```

The second part generates the input values using ```np.linspace```, opens the output image, and evaluates the initial values. Effectively, one set of initial values gets mapped onto each output pixel. 

```python
# use values in the (-2, 2) interval
my_values = np.linspace(start = -2, stop = 2, num=1000)

n_rows = len(my_values)

output_file_name = 'simple_fractal_bw.bmp'

# create a new blank image n_rows by n_rows with the RGB color depth
img = Image.new('1', (n_rows, n_rows))
pixels = img.load()

# enumerate over the values, create complex numbers, and see which values diverge to infinity
for i_enum, i in enumerate(my_values):
    if i_enum % 100 == 0:
        print(i_enum)
    for j_enum, j in enumerate(my_values):
        #print(i_enum, j_enum)
        outcome = iteration_function(z=0, c = complex(i, j), n = 100, display_value=False)
        
        if outcome[0] == 0:
            # 0 if the value does not diverge: black
            #rgb_tuple = (0,0,0)
            rgb_tuple = 0
        else:
            # 1 if the value does diverge: white
            #rgb_tuple = (255,255,255)
            rgb_tuple = 1
        
        pixels[i_enum, j_enum] = rgb_tuple

# save the image
img.save(output_file_name)
```

Most people are familiar with the wild and beautiful intricacy of the Mandelbrot set. The colors are based on how "quickly" a set of initial values diverge to infinity. The visualization in this tutorial is not one of those. This is using NumPy and PIL to make a simple visualization. If you are interested in panning and zooming around the Mandelbrot set, check out this [page](https://math.hws.edu/eck/js/mandelbrot/MB.html).














