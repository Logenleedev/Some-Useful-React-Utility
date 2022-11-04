## Purpose
The purpose of this repo is to help me reference when I write React code. Going through old code and trying to find the target piece is such a pain. So I organize all code snippets which I think will be useful




## 1 Render repetitive components with different props properties
```
    const card = data.map(item => {
      return (
          <div>
             
              <Card 
                  key={item.id}
                  img={item.coverImg}
                  rating={item.stats.rating}
                  reviewCount={item.stats.reviewCount}
                  location={item.location}
                  title={item.title}
                  price={item.price}
                  openspots={item.openSpots}
              />
          </div>
      )
    })
```

## 2 Render repetitive components in ordered list
```
 const noteElement =  props.note.map((item, index) => {
        return (
           
            <div key={item.id} className={styles[`${item.id == props.currentNote.id ? "sidebar--selectedNote-box" : "sidebar--note-box"}`]} onClick={()=>props.setCurrentNoteID(item.id)}>
                <h4>Note {index + 1}</h4>
                <p>{item.body.slice(0, 10) + "..."}</p>
            </div>
        )
    })
```

## 3 Update old list with new element
```
const [notes, setNotes] = React.useState([])
...
function updateNote(text) {
        setNotes(oldNotes => oldNotes.map(oldNote => {
            return oldNote.id === currentNoteId
                ? { ...oldNote, body: text }
                : oldNote
        }))
    }
```

## 4 Insert new element with random id

```
function createNewNote() {
        const newNote = {
            id: nanoid(),
            body: "# Type your markdown note's title here"
        }
        setNotes(prevNotes => [newNote, ...prevNotes])
        setCurrentNoteId(newNote.id)
    }
```