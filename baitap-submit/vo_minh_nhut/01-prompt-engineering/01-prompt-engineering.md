- View following web site which is delimited by triple quotes """https://hoccodeai.com/courses/ai-course/01-1-llm/02-llm-in-action?lesson=advanced-prompt-engineering""”. After that, make six multiple choices questions with 3 wrong answers and one correct answer. Focus on following key notes: using Chain of Thought to help LLM make more precise answers; use affirmative sentence instead of negative sentence; Different among using Zero-shot, one shot, few shot; Advantage of using few shot prompting is helping LLM understand prompt's context better and improve output result; using format in prompt to format output answers. Also give me correct answer after each question.

- Imagine you are going to tell the next part of following stories which is delimited by quotes. Write the next part of the story which has a plot twist that turn out the main character is the antagonist and the protagonist is truly a hero trying to stop the main character from brain wash the whole world. 
"Final Fantasy VII follows the story of Cloud Strife, a mercenary who joins an eco-terrorist group called AVALANCHE, led by Barret Wallace, to stop a corporation called Shinra from exploiting the planet's resources. The group soon discovers that Shinra's plans go beyond energy extraction—they are trying to harness the power of the planet's core to create a weapon of mass destruction. As Cloud and his companions—Tifa Lockhart, Aerith Gainsborough, Red XIII, and others—embark on their journey, they uncover the dark truth about Cloud's past and the mysterious figure, Sephiroth, a former Shinra soldier who is attempting to destroy the planet by summoning a catastrophic event called Meteor. Throughout the adventure, the party confronts themes of identity, loss, and the battle for the planet’s survival. They ultimately face Sephiroth in a final showdown to prevent the destruction of the world. Along the way, Cloud learns more about his own origins and forms deep bonds with his team."

- Take the following JSON data, delimited by triple quotes which contain 20 comments about Captain America: Brave New World movie. Classify them into 3 category: Positive, Negative and Mixed and add a new data field in given JSON name “Rating”:”rated data” for each comment. Then count total number of comment for each category, add new field name “summary” for counted datas. Return all datasets in JSON format
For example:
If comment contains positive words like “top-notch”, “nice”, “good”, it should be positive
If comment contains negative words like “bad”, “underdeveloped”, “predictable”, it should be negative
If comment contains both positive and negative words, it should be mixed
“””
[
    {
        "User": "MarvelManiac",
        "Comment": "Anthony Mackie shines as the new Cap! The action sequences are top-notch, and the political undertones add depth. A must-watch for MCU fans!"
    },
    {
        "User": "FilmCritic101",
        "Comment": "While the film attempts to tackle significant political themes, it often feels heavy-handed. The narrative could have benefited from a more nuanced approach."
    },
    {
        "User": "CasualViewer",
        "Comment": "Enjoyed the movie overall, but it didn't quite capture the magic of the earlier Captain America films. Some scenes felt a bit forced."
    },
    {
        "User": "ActionAddict",
        "Comment": "The fight scenes are exhilarating! Mackie brings a fresh energy to the role, and the supporting cast delivers strong performances."
    },
    {
        "User": "NostalgiaNerd",
        "Comment": "Miss the days of Steve Rogers. Sam Wilson is great, but the film lacks the charm of the original trilogy."
    },
    {
        "User": "PoliticalAnalyst",
        "Comment": "The portrayal of a U.S. president as a supervillain is a bold move, reflecting current societal divisions. It sparks necessary conversations, though it might alienate some viewers."
    },
    {
        "User": "ComicBookPurist",
        "Comment": "Appreciate the nods to classic comics, but some character arcs felt rushed and underdeveloped."
    },
    {
        "User": "DiversityChampion",
        "Comment": "It's refreshing to see a Black Captain America. The film does a commendable job addressing relevant social issues."
    },
    {
        "User": "OldSchoolCap",
        "Comment": "I miss Chris Evans in the role. While Mackie is talented, the film lacks the charisma of its predecessors."
    },
    {
        "User": "StorySeeker",
        "Comment": "The movie tries to juggle too many themes at once, leading to a convoluted plot. A more focused storyline would have been more effective."
    },
    {
        "User": "SuperheroLover",
        "Comment": "An absolute blast! The chemistry between Mackie and the supporting cast is palpable. This movie revitalizes the Captain America legacy."
    },
    {
        "User": "FilmBuff92",
        "Comment": "The inclusion of contemporary political figures as villains felt forced. It detracted from the escapism I seek in superhero films."
    },
    {
        "User": "ThoughtfulCritic",
        "Comment": "The film's ambition is evident, but it bites off more than it can chew. Some plot points feel underexplored."
    },
    {
        "User": "MCUEnthusiast",
        "Comment": "A solid entry in the Marvel universe. It sets up exciting possibilities for future films."
    },
    {
        "User": "CulturalCommentator",
        "Comment": "The portrayal of political figures as villains is a bold move. It reflects current societal divisions, for better or worse."
    },
    {
        "User": "FilmFanatic",
        "Comment": "The pacing is uneven, with some scenes dragging. However, the climax delivers a satisfying payoff."
    },
    {
        "User": "HeroHype",
        "Comment": "Mackie's Captain America brings a new energy to the franchise. The film balances action with character development effectively."
    },
    {
        "User": "CriticalViewer",
        "Comment": "Some plot twists are predictable, and the dialogue occasionally feels clichéd. Not Marvel's best effort."
    },
    {
        "User": "SocialJusticeWarrior",
        "Comment": "The movie bravely addresses systemic issues and representation. It's a step forward for mainstream cinema."
    },
    {
        "User": "IndieFilmSnob",
        "Comment": "MCU movies just aren’t my thing anymore. It’s too formulaic and safe. I miss when they took risks like in Winter Soldier."
    }
]
“””

- Read the following code that is delimited by triple quote and do following task
	1. Explain thoroughly the main purpose of that code includes input, output
	2. Comment each block of code and tell what they do
	3. Check if it has any bug or edge cases that is not tested
	4. Give suggestions to improve its performance and reduce potential bugs
“””
function createJSONObj(layer, hierarchyArr) {
    // Create a JSON object representing a layer with its properties
    var obj = {
        name: layer.name,
        shouldExport: false,
        alwaysVisible: false,
        type: layer.typename + "",
        hierarchy: hierarchyArr.slice(),
        children: []
    };
    return obj;
}

function layerToJSONObject(layer, hierarchyArr) {
    // Convert a layer and its hierarchy into a JSON object
    var obj = createJSONObj(layer, hierarchyArr);
    hierarchyArr.push(obj.name);

    // If the layer is a LayerSet, process its sub-layers
    if (layer.typename === 'LayerSet') {
        for (var i = 0; i < layer.layerSets.length; ++i) {
            var mLayer = layer.layerSets[i];
            var mObj = layerToJSONObject(mLayer, hierarchyArr);
            obj.children.push(mObj);
        }
        for (var i = 0; i < layer.artLayers.length; ++i) {
            var mLayer = layer.artLayers[i];
            var mObj = layerToJSONObject(mLayer, hierarchyArr);
            obj.children.push(mObj);
        }
    }
    hierarchyArr.pop();
    return obj;
}
“””

- I’m going to have a trip to Da Lat from D7, Ho chi minh city next month with 7 adults and 1 2-years old child by car (3 cars) for 4 days. Make a 4 days Itinerary and detailed list of what to go, eat and specific time. Minimal traveling time in one day since there is a toddler, focus on relaxing experience and also buffer hours for unexpected issues, , note the traveling distance from each location to next location. There are some requirements including: return to Ho Chi Minh City before 5 PM; there must be a day to visit Zoodoo Cafe; stay at Ngoc Phat hotel near Xuan Huong lake; attach Google Maps link for each location; Drinking night at one hidden bar such as Mizu bar or a famous bar like Leon; if possible I want to visit Hoan Kiem Lake; double check any suggestion including distance, how can we get there, depart time, arrival time before making any decision; depart from Ho Chi Minh City not earlier than 9 AM; depart from Da Lat not earlier than 10 AM.

- Write a 500 words summary “The Hundred-Year-Old Man Who Climbed Out the Window and Disappeared” book. Then, list down all main characters including their back story, their role and how their impact on the story line. If the book has multiple time lines, also write a 500 words explanation each time line, how they are connected together and how they contribute to the story.