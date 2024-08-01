---
  title: 'JavaTestFile.java'
  description: 'component description'
  pubDate: 'August 1, 2024'
  author: 'Carlos Polanco'
  ---
  
  
  
  # JavaTestFile.java
  # BMI Chart Explanation

The provided code is a Java program that generates a BMI (Body Mass Index) trend chart using the JFreeChart library. Below is a breakdown of the code:

### Libraries Used:
- **JFreeChart**: A popular Java library for creating a variety of charts including pie charts, bar charts, line charts, etc.
- **Swing**: Java's GUI toolkit for creating graphical user interfaces.

### Classes and Methods:
1. **BMIChart Class**:
   - **Constructor**: Initializes the BMIChart object by setting the title and creating the chart panel.
   - **createDataset() Method**: Creates a dataset containing two series of BMI values for two different persons over time.
   - **createChart(XYSeriesCollection dataset) Method**: Creates the actual chart using the dataset provided. It sets up the chart properties like title, axes labels, and orientation.

2. **Main Method**:
   - **SwingUtilities.invokeLater()**: Ensures that the GUI is created and updated on the Event Dispatch Thread (EDT) to prevent any concurrency issues.
   - **BMIChart Object Creation**: Creates an instance of the BMIChart class, sets its properties, and makes it visible.

### Example Usage:
```java
public static void main(String[] args) {
    SwingUtilities.invokeLater(() -> {
        BMIChart example = new BMIChart("BMI Trend Chart");
        example.setSize(800, 600);
        example.setLocationRelativeTo(null);
        example.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
        example.setVisible(true);
    });
}
```

### Purpose:
The code generates a line chart showing the BMI trends of two individuals over a period of time. It visualizes the BMI values on the y-axis against time (in months) on the x-axis.

### How to Run:
To run the code:
1. Ensure you have the JFreeChart library included in your project.
2. Compile and run the BMIChart class.
3. The BMI trend chart window will appear displaying the BMI trends of two persons.

This code provides a simple example of creating a line chart using JFreeChart in Java for visualizing BMI trends.
  
  ## Component Code
  ```jsx
  import org.jfree.chart.ChartFactory;
import org.jfree.chart.ChartPanel;
import org.jfree.chart.JFreeChart;
import org.jfree.chart.plot.PlotOrientation;
import org.jfree.chart.plot.XYPlot;
import org.jfree.chart.renderer.xy.XYLineAndShapeRenderer;
import org.jfree.data.xy.XYSeries;
import org.jfree.data.xy.XYSeriesCollection;
import org.jfree.ui.ApplicationFrame;

import javax.swing.*;
import java.awt.*;

public class BMIChart extends ApplicationFrame {

    public BMIChart(String title) {
        super(title);
        JFreeChart xylineChart = createChart(createDataset());
        ChartPanel chartPanel = new ChartPanel(xylineChart);
        chartPanel.setPreferredSize(new Dimension(800, 600));
        setContentPane(chartPanel);
    }

    private XYSeriesCollection createDataset() {
        XYSeries series1 = new XYSeries("Person 1");
        series1.add(1, 22.5);
        series1.add(2, 23.0);
        series1.add(3, 22.8);
        series1.add(4, 23.5);

        XYSeries series2 = new XYSeries("Person 2");
        series2.add(1, 25.0);
        series2.add(2, 25.4);
        series2.add(3, 25.1);
        series2.add(4, 26.0);

        XYSeriesCollection dataset = new XYSeriesCollection();
        dataset.addSeries(series1);
        dataset.addSeries(series2);

        return dataset;
    }

    private JFreeChart createChart(XYSeriesCollection dataset) {
        JFreeChart chart = ChartFactory.createXYLineChart(
                "BMI Trends",
                "Time (Months)",
                "BMI",
                dataset,
                PlotOrientation.VERTICAL,
                true, true, false);

        XYPlot plot = chart.getXYPlot();
        XYLineAndShapeRenderer renderer = new XYLineAndShapeRenderer();
        plot.setRenderer(renderer);
        return chart;
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            BMIChart example = new BMIChart("BMI Trend Chart");
            example.setSize(800, 600);
            example.setLocationRelativeTo(null);
            example.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
            example.setVisible(true);
        });
    }
}
  ```
  