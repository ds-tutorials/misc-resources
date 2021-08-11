---
title: 'Organizing Information in Spreadsheets'
taxonomy:
    category:
        - docs
subtitle: 'for the Humanities'
intro:
    level: beginner
media_order: 'BookSample_cell.png,omeka.png'
---

Spreadsheets are a wonderful tool for gathering, viewing, sharing, and working with information. As with any tool, learning to use them effectively can make a big difference. In this tutorial we will discuss the structure of an effective spreadsheet, how to deal with certain tricky values you may work with, and some other tips and features for working with spreadsheets.

!!!! ## Learning Objectives
!!!!
!!!! - Describe the basic structure of a spreadsheet.
!!!! - Determine how to organize a complicated dataset.
!!!! - Avoid common pitfalls when creating tables or spreadsheets.
!!!! - Handle tricky information, like dates and null or unknown values.

## Spreadsheet Structure

We will look at several sample spreadsheets to see how we can organize different types of information. Before we look at anything too complex, however, we need to define the basic "data structure" of a spreadsheet.

The Book Sample spreadsheet is a very basic example of standard table listing books.

!!! A quick note on terminology: I am using spreadsheet and table interchangeably here, since a well-organized spreadsheet is a table.

<table>
    <caption>Book Sample</caption>
    <thead>
        <tr>
            <th>Title</th>
            <th>Author</th>
            <th>Date</th>
            <th>Publisher</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>The Visual Display of Quantitative Information</td>
            <td>Edward R. Tufte</td>
            <td>1983</td>
            <td>Graphics Press</td>
        </tr>
      <tr>
        <td>Why We Sleep</td>
        <td>Matthew Walker</td>
        <td>2017</td>
        <td>Scribner</td>
      </tr>
      <tr>
        <td>The Design of Everyday Things</td>
        <td>Don Norman</td>
        <td>2013</td>
        <td>Basic Books</td>
      </tr>
      <tr>
        <td>The Angel and the Assassin</td>
        <td>Donna Jackson Nakazawa</td>
        <td>2020</td>
        <td>Ballantine Books</td>
      </tr>
      <tr>
        <td>New Digital Worlds</td>
        <td>Roopika Risam</td>
        <td>2018</td>
        <td>Northwestern University Press</td>
      </tr>
      <tr>
        <td>The Eye of the World</td>
        <td>Robert Jordan</td>
        <td>1990</td>
        <td>Tor Books</td>
      </tr>
      <tr>
        <td>Weapons of Math Destruction</td>
        <td>Cathy O’Neil</td>
        <td>2016</td>
        <td>Crown</td>
      </tr>
    </tbody>
</table>

There are three components of table structure that are important to note: Columns, rows, and cells.

![Book Sample table with the Author column, Design of Everyday Things row, and Don Norman cell highlighted](BookSample_cell.png)

A column lists some variable, or type of information. In this sample, that information includes title, author, date, and publisher. We could create more columns if we wanted to collect other information about the books - number of pages, ISBN number, subject, and so forth - anything you can think of that you would want to record.

A row lists one observation, or one "item" that we are observing. That "item" could be anything from an observation from hands-on research to information about a concept or physical object. Often, as is the case here, the first row provides column headers instead. This is important for making it clear what each column contains. In this sample, the items we are listing are books, so each row will contain one (and only one) book. This is one of the essential rules for organized spreadsheets: Each row contains information for only one object.

Each intersection of a row and column is a cell. A cell contains the value of the variable specified by the column for the item specified by the row. For example, the cell highlighted here contains the information specified by the Author for the observation of the third item - the book The Design of Everyday Things. In other words, this cell states that the author of The Design of Everyday Things is Don Norman.

The standard rule here is that there should only ever be one value per cell. While this sample conforms to the rule, there is a potential problem area in the author column. You are probably familiar with lots of books and articles that have more than one author. If I want to add a book with multiple authors to this spreadsheet, I have to choose between ignoring all authors other than the first, having multiple authors (values) in a single cell, or restructuring the sheet. As we will see, the last option is typically the best choice, although it will likely take more work. That is why it is important to plan out what information you have and how you will organize it early!

! ### Key Points
!
! - One value per cell
! - One item per row

Another fairly common attribute that shares the same difficulty as author is the tag attribute. Tweets, photographs, artifacts... all kinds of things can have any number of tags. In the next example, we will take a look at how we can address this kind of issue when it comes up.

### Artifacts with Tags

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