---
title: Sort Visualizer
description: A simple app I built a while ago that helps visualize sorting algorithms. Alorithms are implemented from scratch via C#. Most programming languages run the best sort, but it is important to know where things started!
topic: Projects - Click the Title for Images and Explanations
date: Nov. 8, 2022
---

#### [Link: Sort Visualizer on GitHub](https://github.com/kinkeadian25/SortVisualizer)

Sort Visualizer is a simple app I built a while ago that helps people visualize how different sorting algorithms work. All alorithms are implemented from scratch via C#. Nowadays most programming languages help you find the best sort for your needs, but it is important to know where things started!

![Sorting Visualizer Desktop App](/sorting.gif)

## Problem Statement

Understanding how different sorting algorithms work can be a challenge, especially for beginners. The Sort Visualizer app aims to solve this problem by providing a visual representation of various sorting algorithms in action.

## Approach: Using Winforms in C#

Winforms is a graphical user interface class library included as a part of Microsoft's .NET Framework. It provides a platform to develop rich client applications for desktop computers.

The Sort Visualizer app uses Winforms to create an interactive user interface where users can select a sorting algorithm, an array size, and an animation speed. The app then visualizes the sorting algorithm in action, helping users understand how it works.

## Example Sorting Code

```csharp
class BubbleSort : ISortEngine
    {
        private int[] _theArray;
        private Graphics G;
        private int _maxVal;
        Brush WhiteBrush = new SolidBrush(Color.White);
        Brush BlackBrush = new SolidBrush(Color.Black);

        public BubbleSort(int[] theArray, Graphics g, int maxVal)
        {
            _theArray = theArray;
            G = g;
            _maxVal = maxVal;
        }

        public void NextStep()
        {
            for (int i = 0; i < _theArray.Count() - 1; i++)
            {
                if (_theArray[i] > _theArray[i + 1])
                {
                    Swap(i, i + 1);
                }
            }
        }

        private void Swap(int i, int p)
        {
            int temp = _theArray[i];
            _theArray[i] = _theArray[i + 1];
            _theArray[i + 1] = temp;

            DrawBar(i, _theArray[i]);
            DrawBar(p, _theArray[p]);
        }
        private void DrawBar(int position, int height)
        {
            G.FillRectangle(BlackBrush, position, 0, 1, _maxVal);
            G.FillRectangle(WhiteBrush, position, _maxVal - _theArray[position], 1, _maxVal);
        }
        public bool IsSorted()
        {
            for(int i = 0; i < _theArray.Count() - 1; i++)
            {
                if (_theArray[i] > _theArray[i + 1]) return false;
            }
            return true;
        }
        public void ReDraw()
        {
            for (int i = 0; i < _theArray.Count() - 1; i++)
            {
                G.FillRectangle(new System.Drawing.SolidBrush(System.Drawing.Color.White), i, _maxVal - _theArray[i], 1, _maxVal);
            }
        }
    }
```
