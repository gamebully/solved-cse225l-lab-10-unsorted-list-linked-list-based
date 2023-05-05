Download Link: https://assignmentchef.com/product/solved-cse225l-lab-10-unsorted-list-linked-list-based
<br>
In today’s lab we will design and implement the List ADT where the items in the list are unsorted.

<table width="0">

 <tbody>

  <tr>

   <td width="319"><strong>unsortedtype.h </strong> #ifndef UNSORTEDTYPE_H_INCLUDED#define UNSORTEDTYPE_H_INCLUDED template &lt;class ItemType&gt; class UnsortedType{struct NodeType{ItemType info;NodeType* next;};     public:UnsortedType();         ~UnsortedType();         bool IsFull();         int LengthIs();         void MakeEmpty();void RetrieveItem(ItemType&amp;, bool&amp;);void InsertItem(ItemType);         void DeleteItem(ItemType);         void ResetList();void GetNextItem(ItemType&amp;);     private:NodeType* listData;         int length;NodeType* currentPos;}; #endif // UNSORTEDTYPE_H_INCLUDED <strong>unsortedtype.cpp </strong> #include “unsortedtype.h” #include &lt;iostream&gt; using namespace std; template &lt;class ItemType&gt;UnsortedType&lt;ItemType&gt;::UnsortedType(){length = 0;     listData = NULL;     currentPos = NULL;}template &lt;class ItemType&gt;int UnsortedType&lt;ItemType&gt;::LengthIs(){return length;}template&lt;class ItemType&gt;bool UnsortedType&lt;ItemType&gt;::IsFull(){NodeType* location;     try     {location = new NodeType;         delete location;         return false;}catch(bad_alloc&amp; exception){return true;}}</td>

   <td width="393">template &lt;class ItemType&gt;void UnsortedType&lt;ItemType&gt;::InsertItem(ItemType item){NodeType* location;     location = new NodeType;     location-&gt;info = item;     location-&gt;next = listData;     listData = location;     length++;}template &lt;class ItemType&gt;void UnsortedType&lt;ItemType&gt;::DeleteItem(ItemType item){NodeType* location = listData;     NodeType* tempLocation;     if (item == listData-&gt;info){tempLocation = location;         listData = listData-&gt;next;}     else     {while (!(item==(location-&gt;next)-&gt;info))             location = location-&gt;next;         tempLocation = location-&gt;next;location-&gt;next = (location-&gt;next)-&gt;next;}delete tempLocation;     length–;}template &lt;class ItemType&gt;void UnsortedType&lt;ItemType&gt;::RetrieveItem(ItemType&amp; item, bool&amp; found){NodeType* location = listData;     bool moreToSearch = (location != NULL);     found = false;while (moreToSearch &amp;&amp; !found){if (item == location-&gt;info)             found = true;         else         {location = location-&gt;next;moreToSearch = (location != NULL);}}}template &lt;class ItemType&gt;void UnsortedType&lt;ItemType&gt;::MakeEmpty(){NodeType* tempPtr;     while (listData != NULL){tempPtr = listData;         listData = listData-&gt;next;         delete tempPtr;}length = 0;}template &lt;class ItemType&gt;UnsortedType&lt;ItemType&gt;::~UnsortedType(){MakeEmpty();} </td>

  </tr>

  <tr>

   <td width="319"> </td>

   <td width="393">template &lt;class ItemType&gt;void UnsortedType&lt;ItemType&gt;::ResetList(){currentPos = NULL;}template &lt;class ItemType&gt;void UnsortedType&lt;ItemType&gt;::GetNextItem(ItemType&amp; item){if (currentPos == NULL)         currentPos = listData;     elsecurrentPos = currentPos-&gt;next;     item = currentPos-&gt;info; }</td>

  </tr>

 </tbody>

</table>

<strong> </strong>

Generate the <strong>driver file (main.cpp) </strong>where you perform the following tasks. Note that you cannot make any change to the header file or the source file.

<table width="0">

 <tbody>

  <tr>

   <td width="423"><strong>Operation to Be Tested and Description of Action </strong></td>

   <td width="280"><strong>Input Values </strong></td>

  </tr>

  <tr>

   <td rowspan="3" width="423">•     You are given two sequences of integers arranged in ascending order. Your task is to combine the sequences into one ascending sequence. In order to get full marks, you have to make sure that the time complexity of combining two sequences is O(N). You can safely assume that no integer will be repeated. Input starts with a positive integer <strong>m</strong> which specifies the number of elements in the first sequence. Next <strong>m</strong> values are the elements in the first sequence. The next positive integer <strong>n</strong> specifies the number of elements in the second sequence. Next <strong>n</strong> values are the elements in the second sequence. The output is the combined sequence.</td>

   <td width="280">10   1   5   6   10   14   20   25   31   38   4012   2   4   7   9   16   19   23   24   32   35   36   42</td>

  </tr>

  <tr>

   <td width="280"><strong>Expected Output </strong></td>

  </tr>

  <tr>

   <td width="280">1   2   4   5   6   7   9   10   14   16   19   20   23   2425   31   32   35   36   38   40   42</td>

  </tr>

 </tbody>

</table>


