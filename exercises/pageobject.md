## Page Object Model

The image below shows the poll page of the [Simba Organizer](https://github.com/barais/doodlestudent/) application discussed in classes.

![Simba Organizer Poll page](simba-poll-page.png)

Write in this document the interface of a page object class for this page.

## Answer
[Mes réponses](TP_SELENIUM_WALKER_V2/src/main/java/exerciceDeux/PageObjectModell.java)

package exerciceDeux;

import java.util.List;

``java
public interface PageObjectModell {

    // Access menu
        InformationPage createNew();

        String urlToShare();

        String chatRoomURL();

        String padURL();

        // non modifiable element
        String title();

        String place();

        boolean hasMeal();

        List<OptionPanel> options();

        List<List<String>> comments();

        Map<String,List<Boolean>> wichList();

        // Editables
        String nameAndForname();

        PageObjectModell typeNomPrenom(String value);

        String eMail();

    PageObjectModell typeMail(String value);

        boolean hasICS();

    PageObjectModell setHasICS(boolean value);

        boolean hasFavoriteFood();

    PageObjectModell setHasFavoriteFood(boolean value);

        boolean tableauView();

    PageObjectModell setTableauView(boolean value);

        boolean calendarView();

    PageObjectModell setCalendarView(boolean value);

        List<Boolean> wichs();

    PageObjectModell setWichs(List<Boolean> values);

        String authorComments();

    PageObjectModell typeAuthorComments(String value);

        String comment();

    PageObjectModell typeComments(String value);

        // errors
        List<String> errors();

        // buttons
    PageObjectModell submitWichs();
    PageObjectModell submitComments();
    PageObjectModell submitCommentsExpectingErrors();

}
```