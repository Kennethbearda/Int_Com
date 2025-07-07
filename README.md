# Int_Com
const renderAnalysis = (analysis) => {
    if (!analysis || typeof analysis !== 'object') return null;
    return (
      <div>
        {Object.entries(analysis).map(([mainTopic, subtopics]) => {
          // Check if Recommendations already exists as a subtopic
          const hasRecommendations = Object.keys(subtopics).some(
            (k) => k.toLowerCase() === 'recommendations'
          );
          return (
            <div key={mainTopic} style={{ marginBottom: 18 }}>
              <button
                onClick={() => toggleTopic(mainTopic)}
                style={{
                  background: openTopics[mainTopic] ? '#ff9800' : '#232346',
                  color: '#fff',
                  border: 'none',
                  borderRadius: 8,
                  padding: '10px 18px',
                  fontSize: '1.1rem',
                  fontWeight: 600,
                  marginBottom: 6,
                  cursor: 'pointer',
                  width: '100%',
                  textAlign: 'left',
                  transition: 'background 0.2s',
                }}
              >
                {mainTopic}
              </button>
              {openTopics[mainTopic] && subtopics && typeof subtopics === 'object' && (
                <div style={{ marginLeft: 16, marginTop: 8 }}>
                  {Object.entries(subtopics).map(([sub, content]) => (
                    <div key={sub} style={{ marginBottom: 8 }}>
                      <button
                        onClick={() => toggleSubtopic(mainTopic, sub)}
                        style={{
                          background: openSubtopics[mainTopic] === sub ? '#4caf50' : '#2d3545',
                          color: '#fff',
                          border: 'none',
                          borderRadius: 6,
                          padding: '7px 16px',
                          fontSize: '1rem',
                          fontWeight: 500,
                          marginBottom: 2,
                          cursor: 'pointer',
                          width: '100%',
                          textAlign: 'left',
                          transition: 'background 0.2s',
                        }}
