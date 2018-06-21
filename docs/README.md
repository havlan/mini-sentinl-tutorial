# Sentinl watcher tutorial

- [Sentinl documentation](http://sentinl.readthedocs.io/en/latest/)
- [Sentinl github](https://github.com/sirensolutions/sentinl)

## What is a watcher

- A watcher watches over your data, and based on your queries it will trigger an alert.
- How advanced an watcher is relies upon the user or admin of the system.

## How to use Sentinl watchers

- A Sentinl watcher could be used in several ways, the most intuitive way is to create one directly from a visualization or from a visualization saved in your dashboard.
  - In order to do this, you need to create a visualization of your data.
  - My data in all of the tutorials is a randomly generated ip, (Literally bash RANDOM and a timestamp).

- Important aspects:
	- Creating watchers from a visualization:
	- Visualization SPY in the bottom left corner of the visualization.  [Documentation](https://www.elastic.co/guide/en/kibana/current/vis-spy.html)
	![Spy button in the bottom right corner](img/spy_button.png "Spy button in the bottom left corner of the visualization, with a blue square around it.")
	- Visualization SPY tab ![Spy tab](img/spy_tab.png "Visualization SPY contains Several tabs. [Table, Watcher(Sentinl), Request, Response, Statistics]")
	- Watcher tab of Visualization SPY contains a single button which says "Set Alarm".
	- When that button is pressed the query which is generated from the visualization you are currently browsing is passed into a Watcher. (In order to see your query just switch to the request tab)
	- There is also a possibility to browse the response from the elasticsearch server, this could be useful when creating more advanced alerts that involves using JavaScript.

## First watcher

1. From the Visualization SPYs watcher tab click "Set Alarm"
1. You will be presented with a Sentinl watcher wizard.
	- This wizard uses the queries generated from your visualization in it's watcher operations (request tab)
	- The query is based on what you have selected in the time filter, but it will turn these timestamps into relative fields (e.g. "gte":"now-15m/m", "lte":"now/m")
![Spy_wizard](img/watcher_wizard.png "The watcher wizard interface")
	- **Whether this interface looks like this or not is hard to predict, but we've submitted issues and pull requests with our desires. One of them is the dropdown in which you can specify is;  Is above, Is below and Equals.**
1. Specify  attributes for the watcher.
2. Press save and you should be redirected to the Sentinl UI. (The same UI as when you select Sentinl from the menu on the left. See [Understanding the Sentinl UI](#understanding-the-sentinl-ui))

## Understanding the Sentinl UI
![Sentinl user interface](img/sentinl_ui.png "Redirected from the visualization SPY ui. It's also selected on the left menu.")
- The Sentinl UI provides you with the basics of monitoring, maintaining, creating, updating, deleting and testing both watchers and reports.
- In the top right corner of the Sentinl UI there is two buttons, the one you will be using is New, which starts the process of creating a new watcher or alarm.
- When pressing "New" you will be presented with a window/drop down that lets you specify whether it's a new watcher or a new reporter that you wish to create.

## Editing your alarm


## Guides and tutorials
- [Threshold alerting](threshold_alert.md)
- [Anomaly alerting](anomaly_alert.md)
- [Cardinality alerting](cardinality_alert.md)
- [Frequently asked questions](FAQ.md)
