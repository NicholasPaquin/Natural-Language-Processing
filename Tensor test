import plotly
import plotly.graph_objs as go




def create_doc(file):
    with open(file, "r", encoding="UTF-8") as f:
        lines = f.readlines()
        with open("Laws.txt", "a", encoding="UTF-8") as f1:
            f1.writelines(lines)


def word_count():
    word_count = 0
    with open("Laws.txt", "r", encoding="UTF-8") as f:
        for line in f:
            words = line.split()
            word_count += len(words)
    print("Word count: {}" .format(word_count))


def word_count_specified(word):
    with open("Laws.txt", "r", encoding="UTF-8") as f:
        for line in f:
            words = line.split()
            for i in words:
                if i.lower() == word.value:
                    word.frequency += 1
    print("{} appears {} times.".format(word.value, word.frequency))


#noun find doesn't currently work as I would like it to, the noun list I found did not have any of the required nouns
#and I didn't have time to change it/find other data but here is the code


def noun_find(noun):
    noun_search = True
    c_verb_exist = False
    search_left = True
    search_right = True
    count = 1
    count_test = 0
    with open("Laws.txt", "r", encoding="UTF-8") as f:
        for line in f:
            words = line.split()
            for i in range (0, len(words)):
                for j in range (0,3):
                    if words[i].lower() == word_noun_search[j]:
                        print(words[i].lower())
                        while noun_search:
                            while search_left:

                                for k in range(0, len(noun)):
                                    if i-count >= 0 and words[i - count].lower == noun[k].noun:
                                        noun[k].count += 1
                                        noun_search = False
                                        search_left = False
                                        break
                                with open("connecting_verbs.txt", "r", encoding="UTF-8") as c_verbs_doc:
                                    for lines in c_verbs_doc:
                                        c_verbs = lines.split()
                                        for l in c_verbs:
                                            if i-count >= 0 and words[i - count].lower == l.lower():
                                                count += 1
                                                print("is this error? : c_verb found")
                                                c_verb_exist = True
                                                break
                                        if c_verb_exist:
                                            break
                                    if not c_verb_exist:

                                        with open("nouns.txt", "r", encoding="UTF-8") as noun_doc:
                                            for lines in noun_doc:

                                                other_noun = lines.split()
                                                for l in other_noun:
                                                    if i-count >= 0 and l.lower() == words[i - count].lower:
                                                        print("noun searching")
                                                        noun.append(Noun(words[i - count].lower(), 1))
                                                        noun_search = False
                                                        break
                                            search_left = False
                                c_verb_exist = False
                            c_verb_exist = False
                            count = 1
                            while search_right:
                                for k in range(0, len(noun)):
                                    if i+count < len(words) and words[i + count].lower == noun[k].noun:
                                        noun[k].count += 1
                                        noun_search = False
                                        search_right = False
                                        break
                                with open("connecting_verbs.txt", "r", encoding="UTF-8") as c_verbs_doc:
                                    for lines in c_verbs_doc:
                                        c_verbs = lines.split()
                                        for l in c_verbs:
                                            if i+count < len(words) and words[i + count].lower == l.lower:
                                                count += 1
                                                c_verb_exist = True
                                                break
                                        if c_verb_exist:
                                            break
                                    if not c_verb_exist:
                                        with open("nouns.txt", "r", encoding="UTF-8") as noun_doc:
                                            for lines in noun_doc:
                                                other_noun = lines.split()
                                                for l in other_noun:
                                                    if i+count < len(words) and l.lower() == words[i + count].lower():
                                                        noun.append(Noun(words[i + count], 1))
                                                        noun_search = False
                                                        break
                                            search_right = False
                                c_verb_exist = False
                            c_verb_exist = False
                            count = 1
                            c_verb_exist = False

                            search_left = True
                            search_right = True
                        noun_search = True


def clear_doc(file):
    f = open(file, "w")
    f.writelines("")


class WordObj:
    value = "",
    frequency = 0


class Noun(object):
    def __init__(self, noun=None, count=0):
        self.noun = noun,
        self.counter = count


class Search:
    left = True
    right = True


word_noun_search = ["shall", "comply", "report", "should"]
noun_counter = []


shall_obj = WordObj()
comply_obj = WordObj()
report_obj = WordObj()
should_obj = WordObj()
shall_obj.value = "shall"
comply_obj.value = "comply"
report_obj.value = "report"
should_obj.value = "should"


create_doc("Law1.txt")
create_doc("Law2.txt")
create_doc("Law3.txt")
create_doc("Law4.txt")
create_doc("Law5.txt")
word_count()
word_count_specified(shall_obj)
word_count_specified(comply_obj)
word_count_specified(report_obj)
word_count_specified(should_obj)
#noun_find(noun_counter)
#for i in range(0, len(noun_counter)):
    #print("The noun {} appeared {} times".format(noun_counter[i].noun, noun_counter[i].counter))
data = [go.Bar(
            x=[shall_obj.value, comply_obj.value, report_obj.value, should_obj.value],
            y=[shall_obj.frequency, comply_obj.frequency, report_obj.frequency, should_obj.frequency]
    )]

plotly.offline.plot(data, filename='Word-Frequency.html')
clear_doc("laws.txt")
