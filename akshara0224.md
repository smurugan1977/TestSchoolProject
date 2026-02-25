## Page Layout (HTML)

```python

<div id="earnedBadges"></div>

<div id="availableBadges"></div>
```


These are empty boxes on the webpage where badges will be shown.



* &nbsp;   One box = earned badges



* &nbsp;   One box = locked badges



## Getting Badge Data from Backend


```python
const response = await fetch(`${API\_URL}/check-progress`)
```


This asks the server:



&nbsp;   “What badges has this user earned?”



The server sends back JSON data with badge info.



## Showing Badge Progress


```python
const percentage = Math.round((data.earned\_badges / data.total\_badges) \* 100);
```



This calculates how many badges you completed as a percent.



Then it displays:



&nbsp;   Badges earned



&nbsp;   Total badges



&nbsp;   Progress %



## Separating Earned vs Locked Badges

```python

const earnedBadges = badges.filter(b => b.earned);

const lockedBadges = badges.filter(b => !b.earned);
```


This splits the badge list into two groups:



&nbsp;   Earned badges



&nbsp;   Locked badges



## Displaying Badges on Screen

```python

earnedBadges.map(badge => createBadgeCard(badge, true))
```



This loops through each badge and makes a badge card for it.



So every badge becomes a box with:



&nbsp;   Name



&nbsp;   Description



&nbsp;   Requirement



&nbsp;   Earned / Locked status



## Creating a Badge Card (UI Box)

```python

function createBadgeCard(badge, isEarned)

```

This function builds the badge display.



If earned:



&nbsp;   Normal color

&nbsp;   If locked:



&nbsp;   Faded gray



It also shows:



&nbsp;   Badge image (or ? if no image)



&nbsp;   Badge name



&nbsp;   Description



&nbsp;   Requirement



&nbsp;   “✓ Earned” or “Locked”



## Error Message


```python
showError('Please log in to view your badges');
```



If something fails (not logged in, server error), it shows a red message.


## Auto Load When Page Opens

```python
window.addEventListener('DOMContentLoaded', loadBadges);
```


This makes the page load badges automatically when the user opens the page.



