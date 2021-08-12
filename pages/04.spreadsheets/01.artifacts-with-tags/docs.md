---
title: 'Artifacts with Tags'
taxonomy:
    category:
        - docs
---

The Skyrim Museum Sample is a shortened and simplified version of some information that could be uploaded to the content management system Omeka. Omeka allows you to build a basic website with a searchable database containing images or other objects and their metadata (the information about those objects). It is commonly used for archives, and it works well for a variety of digital projects.

This is an image from the Omeka site showing two of the items it contains. (screenshot) If you are interested, you can [explore the Skyrim Museum site](https://theoacker.oucreate.com/skyrim-museum/items/browse) to get an idea of what Omeka can do.

![Omeka website "Browse Items" page showing 2 of 12 items: Crown of Barenziah and Wuuthrad](omeka.png)

This site features a collection of items from the video game Skyrim that would be classified as cultural heritage artifacts, at least if they existed in the real world. Our sample dataset contains a few of these items.

<table>
    <caption>Skyrim Museum Sample</caption>
  <thead>
    <tr>
      <th>Name</th>
      <th>Creator</th>
      <th>Date</th>
      <th>Original Format</th>
      <th>Tags</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Rahgot</td>
      <td>Unknown dragons</td>
      <td>Merethic Era</td>
      <td>Game Object</td>
      <td>armor,dragons,enchanted,Nordic</td>
    </tr>
    <tr>
      <td>Golden Claw</td>
      <td>Unknown</td>
      <td>Unknown</td>
      <td>Game Object</td>
      <td>dragons,Nordic,puzzles</td>
    </tr>
    <tr>
      <td>Mehrunes' Razor</td>
      <td>Mehrunes Dagon</td>
      <td>Unknown</td>
      <td>Game Object</td>
      <td>Daedric,dagger,enchanted,one-handed,weapon</td>
    </tr>
    <tr>
      <td>Auriel's Bow</td>
      <td>Anuiel</td>
      <td>Dawn Era</td>
      <td>Game Object</td>
      <td>bow,enchanted,prophecy,two-handed,weapon</td>
    </tr>
    <tr>
      <td>Wuuthrad</td>
      <td>Yngol</td>
      <td>Merethic Era</td>
      <td>Game Object</td>
      <td>axe,Nordic,two-handed,weapon</td>
    </tr>
  </tbody>
</table>

In this dataset we have name, creator, date, original format, and tags. You may have noticed that the Tags column is breaking the rule of one value per cell. This illustrates one of the rare cases when it is good to break the rule. When uploading this data to Omeka, the Omeka importer will recognize the Tags column and separate out the list of tags as individual items. This means that the end result will not have all the tags mashed together like we see here.

That is great for importing data into Omeka. It is not so great for other potential uses. What if we want to analyze the data outside of Omeka using some other type of software? For a simple example, maybe we want to count how many objects have the "enchanted" tag. It is simple enough to count by hand, since this is such a tiny dataset. In a larger dataset however, I might have closer to five hundred items than five. With such a dataset, there would be no easy way to count the number of objects with any given tag.

Other potential avenues for analysis include:

- How many tags does each item have?
- What are the most common tags?
- Which tags tend to show up together?

With the current structure, we have no reasonable way to get this information.

So what is the solution?

#### Variable List of Generic Columns

The first option we will consider is adding a list of however many generic columns we end up needing, as shown below.

<table>
    <thead>
      <tr>
        <th>Name</th>
        <th>Creator</th>
        <th>Date</th>
        <th>Original Format</th>
        <th>Tag 1</th>
        <th>Tag 2</th>
        <th>Tag 3</th>
        <th>Tag 4</th>
        <th>Tag 5</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Rahgot</td>
        <td>Unknown dragons</td>
        <td>Merethic Era</td>
        <td>Game Object</td>
        <td>armor</td>
        <td>dragons</td>
        <td>enchanted</td>
        <td>Nordic</td>
        <td></td>
      </tr>
      <tr>
        <td>Golden Claw</td>
        <td>Unknown</td>
        <td>Unknown</td>
        <td>Game Object</td>
        <td>dragons</td>
        <td>Nordic</td>
        <td>puzzles</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>Mehrunes' Razor</td>
        <td>Mehrunes Dagon</td>
        <td>Unknown</td>
        <td>Game Object</td>
        <td>Daedric</td>
        <td>dagger</td>
        <td>enchanted</td>
        <td>one-handed</td>
        <td>weapon</td>
      </tr>
      <tr>
        <td>Auriel's Bow</td>
        <td>Anuiel</td>
        <td>Dawn Era</td>
        <td>Game Object</td>
        <td>bow</td>
        <td>enchanted</td>
        <td>prophecy</td>
        <td>two-handed</td>
        <td>weapon</td>
      </tr>
      <tr>
        <td>Wuuthrad</td>
        <td>Yngol</td>
        <td>Merethic Era</td>
        <td>Game Object</td>
        <td>axe</td>
        <td>Nordic</td>
        <td>two-handed</td>
        <td>weapon</td>
        <td></td>
      </tr>
    </tbody>
</table>

Here we have created five columns so that each tag is in its own cell and column. There are several major issues with this. First, the number of tags a given object has is variable. At the moment we only need five columns, since the most tags any of these items have is five, but we cannot count on that. We might end up with an item that has ten or even twenty tags. In addition, this structure does not help us at all in analyzing the data. Consider the "simple" question of how many objects have the "enchanted" tag. Again, it is easy enough to count by hand with a dataset of only five objects. If I had a larger dataset and wanted to use some software to find this number, however, it would be rather complicated to explain what I needed to the software. I would have to list out each tag column (Tag 1, Tag 2, Tag 3, and so on) and tell the program to check each of them, as "enchanted" could show up in any of them.

This might seem like a minor hassle with the data we have. Listing the five columns is only slightly annoying, but imagine if there were twenty columns instead, or if we wanted to make a chart showing how many times each tag shows up. While these are not the only issues, they are enough to indicate that this is **_not_** the solution.

#### Long List of Specific Columns

Our second option is a slightly different take on the first. We still create extra columns, but this time we create a specific column for each potential value. In this case, we need a column for each different tag used in the dataset.

<table>
    <thead>
      <tr>
        <th>Name</th>
        <th>Creator</th>
        <th>Date</th>
        <th>Original Format</th>
        <th>armor</th>
        <th>axe</th>
        <th>bow</th>
        <th>Daedric</th>
        <th>dagger</th>
        <th>dragons</th>
        <th>enchanted</th>
        <th>Nordic</th>
        <th>one-handed</th>
        <th>prophecy</th>
        <th>puzzles</th>
        <th>two-handed</th>
        <th>weapon</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Rahgot</td>
        <td>Unknown dragons</td>
        <td>Merethic Era</td>
        <td>Game Object</td>
        <td>yes</td>
        <td>no</td>
        <td>no</td>
        <td>no</td>
        <td>no</td>
        <td>yes</td>
        <td>yes</td>
        <td>yes</td>
        <td>no</td>
        <td>no</td>
        <td>no</td>
        <td>no</td>
        <td>no</td>
      </tr>
      <tr>
        <td>Golden Claw</td>
        <td>Unknown</td>
        <td>Unknown</td>
        <td>Game Object</td>
        <td>no</td>
        <td>no</td>
        <td>no</td>
        <td>no</td>
        <td>no</td>
        <td>yes</td>
        <td>no</td>
        <td>yes</td>
        <td>no</td>
        <td>no</td>
        <td>yes</td>
        <td>no</td>
        <td>no</td>
      </tr>
      <tr>
        <td>Mehrunes' Razor</td>
        <td>Mehrunes Dagon</td>
        <td>Unknown</td>
        <td>Game Object</td>
        <td>no</td>
        <td>no</td>
        <td>no</td>
        <td>yes</td>
        <td>yes</td>
        <td>no</td>
        <td>yes</td>
        <td>no</td>
        <td>yes</td>
        <td>no</td>
        <td>no</td>
        <td>no</td>
        <td>yes</td>
      </tr>
      <tr>
        <td>Auriel's Bow</td>
        <td>Anuiel</td>
        <td>Dawn Era</td>
        <td>Game Object</td>
        <td>no</td>
        <td>no</td>
        <td>yes</td>
        <td>no</td>
        <td>no</td>
        <td>no</td>
        <td>yes</td>
        <td>no</td>
        <td>no</td>
        <td>yes</td>
        <td>no</td>
        <td>yes</td>
        <td>yes</td>
      </tr>
      <tr>
        <td>Wuuthrad</td>
        <td>Yngol</td>
        <td>Merethic Era</td>
        <td>Game Object</td>
        <td>no</td>
        <td>yes</td>
        <td>no</td>
        <td>no</td>
        <td>no</td>
        <td>no</td>
        <td>no</td>
        <td>yes</td>
        <td>no</td>
        <td>no</td>
        <td>no</td>
        <td>yes</td>
        <td>yes</td>
      </tr>
    </tbody>
</table>

This structure improves our ability to perform some types of analysis, though it causes issues with others. More importantly, however, this is simply not feasible. We have to add one column for each tag. With only five items, each of which has at most only five tags, we already have thirteen different possible tags. With a full dataset, we would have a lot more. There are some cases where adding specific columns like this is a good solution (we will see one in a different example), but this is clearly not one of those.

#### Multiple Spreadsheets

Finally, we have our only real option: Splitting the data into two different spreadsheets/tables.

The first table, Objects, contains all of the artifact information except for tags. In fact, it is literally the same table we started with, but with the Tags column removed.

<table>
    <caption>Objects</caption>
  <thead>
    <tr>
      <th>Name</th>
      <th>Creator</th>
      <th>Date</th>
      <th>Original Format</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Rahgot</td>
      <td>Unknown dragons</td>
      <td>Merethic Era</td>
      <td>Game Object</td>
    </tr>
    <tr>
      <td>Golden Claw</td>
      <td>Unknown</td>
      <td>Unknown</td>
      <td>Game Object</td>
    </tr>
    <tr>
      <td>Mehrunes' Razor</td>
      <td>Mehrunes Dagon</td>
      <td>Unknown</td>
      <td>Game Object</td>
    </tr>
    <tr>
      <td>Auriel's Bow</td>
      <td>Anuiel</td>
      <td>Dawn Era</td>
      <td>Game Object</td>
    </tr>
    <tr>
      <td>Wuuthrad</td>
      <td>Yngol</td>
      <td>Merethic Era</td>
      <td>Game Object</td>
    </tr>
  </tbody>
</table>

We can then deal with the Tags column in a second spreadsheet. Here, each row pairs one object and one tag. Every object gets one row for each of its tags. For example, Auriel's Bow has five tags, so it gets five rows in this new table.

<table>
    <caption>Tags</caption>
    <thead>
      <tr>
        <th>Name</th>
        <th>Tag</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Rahgot</td>
        <td>armor</td>
      </tr>
      <tr>
        <td>Rahgot</td>
        <td>dragons</td>
      </tr>
      <tr>
        <td>Rahgot</td>
        <td>enchanted</td>
      </tr>
      <tr>
        <td>Rahgot</td>
        <td>Nordic</td>
      </tr>
      <tr>
        <td>Golden Claw</td>
        <td>dragons</td>
      </tr>
      <tr>
        <td>Golden Claw</td>
        <td>Nordic</td>
      </tr>
      <tr>
        <td>Golden Claw</td>
        <td>puzzles</td>
      </tr>
      <tr>
        <td>Mehrunes' Razor</td>
        <td>Daedric</td>
      </tr>
      <tr>
        <td>Mehrunes' Razor</td>
        <td>dagger</td>
      </tr>
      <tr>
        <td>Mehrunes' Razor</td>
        <td>enchanted</td>
      </tr>
      <tr>
        <td>Mehrunes' Razor</td>
        <td>one-handed</td>
      </tr>
      <tr>
        <td>Mehrunes' Razor</td>
        <td>weapon</td>
      </tr>
      <tr>
        <td>Auriel's Bow</td>
        <td>bow</td>
      </tr>
      <tr>
        <td>Auriel's Bow</td>
        <td>enchanted</td>
      </tr>
      <tr>
        <td>Auriel's Bow</td>
        <td>prophecy</td>
      </tr>
      <tr>
        <td>Auriel's Bow</td>
        <td>two-handed</td>
      </tr>
      <tr>
        <td>Auriel's Bow</td>
        <td>weapon</td>
      </tr>
      <tr>
        <td>Wuuthrad</td>
        <td>axe</td>
      </tr>
      <tr>
        <td>Wuuthrad</td>
        <td>Nordic</td>
      </tr>
      <tr>
        <td>Wuuthrad</td>
        <td>two-handed</td>
      </tr>
      <tr>
        <td>Wuuthrad</td>
        <td>weapon</td>
      </tr>
    </tbody>
</table>

The two spreadsheet connect by using the artifact name. In the fifth row of the Tags table, we pair the Golden Claw with the dragons tag. Then we pair it with Nordic, and then with puzzles. Because the "Name" variable is unique to each of our objects - for example, we only have one object with the name Golden Claw - we can use this to clearly identify which object a given tag belongs to. There is no question that the three tags just mentioned (dragons, Nordic, puzzles) all belong to the object called Golden Claw.