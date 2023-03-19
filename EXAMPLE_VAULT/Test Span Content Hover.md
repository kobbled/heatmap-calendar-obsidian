```dataviewjs

dv.span("**🏋️ Exercise 🏋️**")

const calendarData = {
    year: 2022,
    colors: {
        red: ["#ff9e82","#ff7b55","#ff4d1a","#e73400","#bd2a00",]
    },
    entries: []
}

const convertMinutes = (minutes)=>{
	var timeformat = "mm";
	if (minutes === null) {
		return "";
	}
	return `${minutes/60000} min`;
}

for(let page of dv.pages('"daily notes"').where(p=>p.exercise)){
    //dv.span("<br>" + convertMinutes(page.exercise))

    calendarData.entries.push({
        date: page.file.name,
        intensity: page.exercise,
        content: dv.span(`Exercised  ${convertMinutes(page.exercise)} on ${page.file.name} <br/> Note: [[${page.file.name}]]`)
    })
       
}

renderHeatmapCalendar(this.container, calendarData)

```