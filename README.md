# FreeCodeCamp advanced algorithm scripting project - no repeats please - Javascript solution
link: https://www.freecodecamp.org/challenges/no-repeats-please


function permAlone(str) {
  
  var regExp = /(\w)\1+/g;
  
  function getAllPermutations (text) {
    var result = [];
    
    if (text.length === 1) {
      result.push(text);
      return result;
    }
    
    for (var i = 0; i < text.length; i++) {
      var first = text[i];
      var remains = text.substring(0, i) + text.substring(i + 1);
      var innerPermutation = getAllPermutations(remains);
      for (var j = 0; j < innerPermutation.length; j++) {
        result.push(first + innerPermutation[j]);
      }
    }
    
    return result;
  }
  
  var allPermutations = getAllPermutations(str);
  var result = allPermutations.filter(function(item) {
    return !item.match(regExp);
  });
  
  return result.length;
}

permAlone('aab');
