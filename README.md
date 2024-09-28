
# enimation

**enimation** is a customizable loading tool for Python projects that allows users to implement various loading animations with extensive customization options. This package enhances user experience during data processing, API calls, or any time-consuming tasks by providing visual feedback.

## Features

- **Customizable Loading Animations**: Choose from multiple loading animations, or define your own.
- **Duration Control**: Specify the update interval for the loading animation.
- **Decorator Support**: Easily add loading animations to any function with a simple decorator.

## Installation

You can install the package using pip:

```bash
pip install enimation

Or if you are developing locally, you can install it in editable mode:

pip install -e .
```

## Basic Usage

To get started with the loading tool, follow these simple steps:

1. Import the CustomLoading Class

First, import the CustomLoading class from the package:

```python
from enimation import CustomLoading
```

2. Create an Instance of CustomLoading

Create an instance of the CustomLoading class, optionally providing a custom animation function and interval:

```python
loader = CustomLoading(interval=0.1)  # 0.1 seconds update interval
```

3. Start the Loading Animation

Call the start() method to begin the loading animation in a separate thread:

```python
loader.start()
```

4. Stop the Loading Animation

When the task is completed, call the stop() method to stop the animation:

```python
loader.stop()
```

## Example

Here’s a simple example of using CustomLoading:

```python
import time
from enimation import CustomLoading

def long_running_task():
    time.sleep(5)  # Simulate a long-running task

loader = CustomLoading()
loader.start()
long_running_task()
loader.stop()
```

## Advanced Usage

# Custom Animations

You can create your own custom loading animations by defining a function that updates the loading display. For example:

```python
def my_custom_animation():
    frames = ['🌟', '✨', '🌈', '💫']
    while not loader.stop_event.is_set():
        for frame in frames:
            print(f'\rLoading {frame}', end='', flush=True)
            time.sleep(0.5)

loader = CustomLoading(animation_function=my_custom_animation, interval=0.5)
loader.start()
long_running_task()
loader.stop()
```

# Using the Loading Decorator

The loading decorator can be used to automatically add loading animations to your functions. Here's how to use it:

```python
from enimation import loading

@loading()  # Use default loading animation
def long_running_task():
    time.sleep(5)  # Simulate a long-running task

long_running_task()
```

# Customizing the Decorator

You can also pass a custom CustomLoading instance to the decorator:

```python
custom_loader = CustomLoading(animation_function=my_custom_animation)

@loading(custom_loading_instance=custom_loader)
def another_long_running_task():
    time.sleep(10)  # Simulate another long-running task

another_long_running_task()
```

# Integration with Asynchronous Tasks

You can run the loading animation in a separate thread alongside your main tasks. For example:

```python
import threading

def long_running_task():
    time.sleep(10)

loader = CustomLoading()
threading.Thread(target=long_running_task).start()
loader.start()
loader.stop()
```

## Contributing

If you'd like to contribute to enimation, please fork the repository and submit a pull request. We welcome contributions of all kinds, including bug fixes, documentation improvements, and new features.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Contact

For any inquiries or suggestions, feel free to reach out to:

hasan: hasanfq818@gmail.com

GitHub: [here](https://github.com/Kamanati/enimation)

# enimation
An animation function for python to higly customize you code with bueatyfull animation
